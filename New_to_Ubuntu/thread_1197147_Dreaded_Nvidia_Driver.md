---
title: "Dreaded Nvidia Driver"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-06-25
[SIZE=3]Ubuntu 9.04 32 bit
As far as updating to the proprietary Nvidia driver version 180. If I do it using the System->Administration->Hardware Drivers route, [/SIZE][SIZE=4][SIZE=3]I end up with the system not being able to boot. It freezes while displaying the line "checking battery state..." I haven't figured out what to do then so I just keep re-installing and trying different things. I noticed there is a command line way to upgrade this driver as well.

Why are there two diff routes and what is the difference? 
How do I determine which way is the safest to upgrade for me?

Thanks[/SIZE]


[/SIZE]

---

### Post by pablolie on 2009-06-25
the 180 driver (sorry for typo) works perfectly on my machine with 9.04 - any other exotic components? 180 seems very solid -and nvidia drivers seem to always have been- on my machines, the only rough edges have been dual monitor configs and what not.

---

### Post by juanoleso on 2009-06-25
> **ncc1701e said:**
> [SIZE=3]
Why are there two diff routes and what is the difference?
How do I determine which way is the safest to upgrade for me?
[/SIZE]


If you post the two ways that you know of then the forum might be able to determine this.

You could also post your hardware specs as that will give us more information to work with.

---

### Post by ncc1701e on 2009-06-25
the 80 mdriver is it the same as the 180? and where do I get it?

---

### Post by ncc1701e on 2009-06-25
Being a newbie to Ubuntu,

The two different routes of updating the video driver that I know are:

1. Through the System->Administration->Hardware Drivers

This caused a major problem in my system which is:

Intel Core Duo 2.66GHZ
2.25 MB RAM
Ubuntu 9.04 32 bit
2 Nvidia GeForce 8600 512MB in SLI

I updated the Nvidia driver to the 180 which was the recommended one. It asked for a restart to take effect so I did and instead of booting normally the system hung up while
displaying a bunch of text lines about the different services it was starting and the last
line read "Checking battery state...". It would not go any further.

To resolve the issue I turned to the forums and tried various thing that I came to learn and I though made sense. I tried to boot into recovery mode and tried the "fix x-server" option that did not change anything.
I then tried to boot into recovery mode and chose to "fix broken packages". that did not change anything.
I then booted to a shell as root through the recovery mode, logged in and typed "startx" that gave me "FATAL ERROR: no screens found".

2. The second method to update the video drivers that I know of is a method I came across while trying to find out how to get my desktop back after the first method broke it.
And this method is to basically get into the CLI download the nvidia driver using wget then install it in text mode using the "sudo sh" command on the downloaded file. I ran into problems with this method because while the download of the driver went fine, when installing it after accepting the license agreement it would say something about the kernel interface not being there and asking me if I wanted the driver install utility to compile one so I chose "yes" and it did. It told me the driver was successfully installed. It then asked if I wanted a new xorg.conf file created based on the new configuration and I chose to do so. Following that I tried to to the "nvidia-config -a" to configure it to work with both of my cards and thats when it said that the kernel version was 180.11 and the driver version was 180.22 and that the versions much match and told me to make sure the version numbers matched and said it could not honor the option "enable all GPUs" . Being the newbie that I am I was a bit lost.

So I gave up after a few days of browsing around the forums and re-installed ubuntu 9.04 32bit and so far I have not updated my nvidia driver and things are going ok. But when I try to run the x-plane flight simulator my video is really messed up as I showed in the screen shot in the starting of this thread and the framerate is terrible. Sound is ok though.

One interesting this is that even after taking one of my video cards out of the sytem physically and updating to the 180 driver using method 1 produced the exact same results as the first time around so now I know that its not the fact that I have two cards that the problem.

So, in short, I'd like to update my nvidia drivers to the latest and have it configured to work with both cards in my system because its dual boot and I like to use SLI in windows.

Thanks.

---

### Post by pablolie on 2009-06-25
> **ncc1701e said:**
> the 80 mdriver is it the same as the 180? and where do I get it?

corrected to 180 - the one you have. worked stably out of the box for me.

---

