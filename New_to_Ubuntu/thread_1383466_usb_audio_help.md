---
title: "usb audio help"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by p1554nt on 2010-01-17
hello. i'm only a slight beginner. i have been using since intrepid & dapper. since juanty i have been using booting into juanty exclusively for 9 months unless i am forced into xp. now i'm on karmic. i also have converted my 55 year old father.
my main pc died so i am using some old laptops lying around.

i have a m-audio sonica. at first i was unable to get it working.
then juanty came out & the laptop i was using wouldn't work with the laptops onboard sound. i tried my m-audio sonica again & it was working but barely.
the sound was really low & clipping. when looking @ audio hardware properties it showed only 2 channels.
i rebooted later the sound stopped working. i looked @ the properties & it shows all the channels. but  under output it only gives me "dummy output"

i started using another laptop that the on board worked. it only showed 2 channels unlike when it is atached to the laptop i want to use it on.
it wasn't as powerful & the sound kept dropping out unless i rebooted so i tried the sonica again.

i looked around as i do with all my problems with ubuntu that i fixed & saw that i needed "madfuload"
i installed the deb from here
[https://launchpad.net/ubuntu/+source/madfuload](https://launchpad.net/ubuntu/+source/madfuload)

it worked.

so i go back to my other laptop & try the same thing & it will not work.
i have tried to uninstall "madfuload" then reinstall to no avail.

is there a way to get some files & setting set like my other laptop to make this work?

on the one not working lsusb gives me the output
Bus 002 Device 002: ID 0763:2007 Midiman M-Audio Sonica Theater

if that is any help.

thank you

---

### Post by gordintoronto on 2010-01-17
Have you looked at this thread?
[http://ubuntuforums.org/showthread.php?t=846621](http://ubuntuforums.org/showthread.php?t=846621) 

Madfuload is actually available in Synaptic, which makes it easier to uninstall.

---

