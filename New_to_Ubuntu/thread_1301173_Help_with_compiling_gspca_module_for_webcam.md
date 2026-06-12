---
title: "Help with compiling gspca module for webcam"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-10-25
I must compile a webcam driver into my kernel. I don't know how to do that. The README says:

[COLOR="Red"]The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your kernel, and updated the dependencies:

'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as was used to compile your kernel. Not doing so can create incompatible binaries.

as root go to gspcav1 directory and run:

./gspca_build 

if all goes right the module is compiled and loaded in memory
if not, errors messages can be found in kgspca.err You should post this file to the maintainer or in the sourceforge project bugs report. <http://sourceforge.net/projects/spca50x/>.


Trying a v4l app

be sure to have libsdl installed with the header and go to gspcagui directory 

then
make
as root
make install

Plug your webcam and run gspcagui -d /dev/video0

adjust video0 to your hardware. Press the G button and wait for the webcam probe you can now play, the two windows are active 
mouse can be used to select a Region of Interess within the grabbing windows then press the center of the pad to zoom:)
Picture and avi are implemented just press the button to start/stop[/COLOR]

Can someone with some experience with type of work give me some help? I'm not afraid to use the terminal, but I must know what I'm doing and the foregoing is way beyond my limited understanding. I have done some ./make ./make install and such, but forget what to do to remove the unnecessary stuff and the instructions above don't talk about that. I guess the fellow-programmers know there way around more than I. Thanks for your time reading this.

---

