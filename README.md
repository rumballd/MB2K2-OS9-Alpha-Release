# MB2K2-pre-release
 pre release files for the MB2K2

These are the files for the alpha release of OS-9 L1 for the MB2K2.

There will be bugs!


To use flash the Xmos firmware and PROMdisk image with the Xmos tools command shell and xFlash command:-

xflash --verbose --no-compression --factory <image.xe> --boot-partition-size 0x80000 --data <promdisk.dsk>

where <image.xe> and <promdisk.dsk> are the locations of the .xe and .dsk files. Note that it will take a while to flash with the block count running to about 0x00366500 ish.

If you don't have the Xmos tools installed, the 'Firmware Build and Flashing guide' explains how to install the xTIMEComposer toolchain.


Build notes

Both the FLEX and OS9 OSs and are in the same build/flash image and the PROMdisk is a combination of a FLEX disk image followed by an OS9 disk image. OS9 is 'preloaded' into RAM when the MB2K2 starts up whilst the FLEX PROMdisk has FLEX.cor.

Boot from MON09 with the ‘BO’ command for OS9 or the ‘BF’ command for FLEX. FLEX should run just as before but note that booting FLEX will overwrite the OS9 kernel requiring a restart (power off and on) of the MB2K2 before booting into OS9.

After OS9 boots the red 6809 LED will flash once a second to show that the clock is running and the date and time are set from the RTC so there's no need to set the clock.

The supported drive types are:-
    PROMdisk - /d0
    RAMdisk - /r0    note: Format the RAMdisk first before use with the 'format' command.  (format /r0)
    FLEXNet - /h0   note: mount a remote volume with 'rmount /h0 <image name>'  (only /h0 is supported at the moment)
    
floppymaint.exe and FLEX-0S9-Net.exe are courtesy of Mike Evenson



