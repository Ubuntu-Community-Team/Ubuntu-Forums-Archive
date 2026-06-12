---
title: "A really easy way to get a silver USB ADSL speedtouch modem working"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by vangoss on 2008-04-07
Hello everybody, I am real new to this, and I’m hoping I don't give up before I can get ubuntu working

I'm sure you've all heard it before, I’m from the windows vista camp, I have decided to try and give up with these Microsoft products now though, automatic update killed my computer a few weeks ago, and I have tired updating windows to service pack 1, with no luck, it continues to fail.

The whole thing is too gimmicky for my tastes, and I want to give Linux another go,
I say another go because the last time I used it the wireless card wouldn't work so I gave up after a week of trying to find the solution, I only get the chance to mess around with the computer like this every now and then, 

Here is hoping this time round things are different. Well I use another internet provider now (moved home) and I use a USB ADSL speedtouch modem, a 330 one, it’s also a nice silver colour.

i have read one tutorial but it got way to deep

i know we need more patience to get Linux working , because most of the drivers are for windows but this was kind of over the top, I don't know how you expect people who don't work for a IT company to be able to make use of this.

it told me to go to a website, download a script, then get another file,
then told me to go into root, i have no idea what the root password is, and the script never does anything any way, never stops to ask me any details, like what my user name is, like what my password is, nope, it just wizzies through and thats that,

i know you lot see a few scripts, and root logins, as easy stuff, but i don't, it took me half hour to work out that a root file system is a slash, how on earth am I meant to know what this means?:
"Please select the root file system or installation cannot continue"
No one tells me that root is a slash.

I think you get the idea, i get stuck when its telling me to do something that i got no idea what it means

I feel quite dumb really,

With windows they have little descriptions for everything, in Linux its half guess work for me

I really want to give this a go, so i would really appreciate it if someone could show me an easy way to get something as simple as the internet working, thanks

i am with homecall, in the uk, i have no idea what the vip numbers are

Also, another thing making this more frustrating, the screen resolution has now decided to stay at 640, it was working ok then decided not to work, so I’m stuck at 640, it won’t change at all

i have a mobile geforce series 7 graphics card


thankyou

from Joseph Goss

---

### Post by plucky on 2008-04-07
For Speedtouch 330 modem see this [link](http://www.squeezedonkey.com/wiki/linux/index.php?title=How_to_Try_it) to get the .deb file and instructions to install for Ubuntu.

And this [thread](http://ubuntuforums.org/showthread.php?t=585647&highlight=speedtouch)
for giving feedback to the person who wrote the application.


> the screen resolution has now decided to stay at 640

Open a terminal and try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and then restart your X Gui with Ctrl-Alt-Backspace which will log you off the system and restart the X server.


Good Luck

---

