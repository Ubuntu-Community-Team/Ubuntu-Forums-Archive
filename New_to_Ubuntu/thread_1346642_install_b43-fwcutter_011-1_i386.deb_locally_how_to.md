---
title: "install b43-fwcutter_011-1_i386.deb locally? how to?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by woodnymph on 2009-12-05
just installed a fresh karmic, but the restricted driver packages are not is the release - i have to update first to see the bc43 drivers .. catch-22 - no wifi, but need internet to get wifi.  i do not have a wired connection.  

i do have the b43-fwcutter_011-1_i386.deb on my usb stick.  how do i unpackage this locally so that all the files get to the proper places so that they can be read and get this chip working?

i am a novice on the command line, so if that is the best solution, please be specific with commands.  thanks for any help.

---

### Post by mikewhatever on 2009-12-05
Double clicking the deb file should do the job, provided all dependencies are satisfied.

---

### Post by woodnymph on 2009-12-07
i found [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"), which has about 3/4 the way down an option for "No Alternate Internet Access" (copied below)


the difficulty i have found generally as a new terminal user is that often the command line instructions - while good - assume some base knowledge which i do not have.  in this case, the solution worked perfect, but didn't say much about where and how to do some of the basics.  as you see in #3 below, it just says, "Execute the following necessary commands on the files above manually."  for a user like me, i don't know what that is.  (i will fill in some of what i did ..)


**No Alternate Internet Access**

If you don't have any other means of internet access on your computer, you will have to:

   1. Install b43-fwcutter (without the firmware downloading and being set up) which should be located on the Ubuntu {9.04} install disc (add it as a repository in Synaptic) or from /var/cache/apt/archives on an Ubuntu computer with b43 installed.

   2. Obtain
          * [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and
          * [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2). 

   3.  Execute the following necessary commands on the files above manually

** this mean put the two above files in your /lib/firmware folder, which i was able to do in karmic9.10 by opening the folder as root in the gui- i have not figured out yet how to do this all from a command line.  so being able to open folders as root in the gui is a nice feature for users like me who are learning bits of terminal code as i go .. it is little things like this that have stumped me in the past.

Secondly, before running the commands below from terminal, i found the need to move into that directory by the cd 'change directory' command - in the terminal
sudo cd /lib/firmware

now you can run the rest. i got to all this with trial and error and luck as a terminal newby**

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

Try restarting your computer to verify the installation went correctly.

If it fails to work after a restart try 'sudo modprobe b43'. Then add the line 'b43' to 'sudo gedit /etc/modules'.

---

