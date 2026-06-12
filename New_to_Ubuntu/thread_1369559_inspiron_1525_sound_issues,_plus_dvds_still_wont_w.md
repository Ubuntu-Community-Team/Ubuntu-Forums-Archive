---
title: "inspiron 1525 sound issues, plus dvds still wont work...."
date: 2010-01-01
forum: New to Ubuntu
---

### Post by AmyB on 2010-01-01
Hi all, 

i have done the upgrade from 7.10 to 8.04 via the upgrade system, not the CD install. I am struggling with the sound and playing DVD's.

I have been working on this Dell inspiron 1525 for a few weeks now as this is the first clean install that i could get to work as there has been numerous issues.

I have tried to read as many posts as i could but i still am struggling. I did read another post that was very helpful for the lack of sound issue, adding the ppa etc. however i got as far as loading 2 of the 3 available files, the 3rd, the hsfmodem, is refusing to load. the message i recieve is:
E: hsfmodem-base-dkms: subprocess post-installation script returned error exit status 7

If i look at the detail it says that: The directory /lib/modules/2.64..2-61-generic does not exist, and it cannot load onto a non existent kernal.

i am now lost with this issue!

the second issue is when a DVD is loaded i asked it to chose the codecs for the DVD (i have tried many different DVD's at this point) and it goes to find them, adds them, it all looks ok, then when it goes to play it says:

Failed to connect to stream - invalid Argument

that is the message i get for all DVD's that i try and play.

In general i am a newby to ubuntu, and laptops, but pc's in general i know (sadly windows based platforms are all i learned) so as a favour to a friend of mine i am trying to sort out his laptop for him, and learing ubuntu along the way (he knows nothing at all about pc's)

I refuse to let this get the better of me, but i am thinking that i might need to just do a CD install as was suggested in another post as opposed to working through all of the errors that i am facing (my preferred method is to work through them as i want to learn the workarounds), but after 2 weeks i am ready to cry, scream, chuck the laptop out the window. i dont care what order it happens in. 

the laptop had onboard sound that is enabled (i checked the bios before i did anything else) 

can anyone suggest something or let me know what i might have inadvertently done wrong?

is the fresh CD install the best option at this point?

thanks in advance for the advice, and sorry for the exceedingly long post :)

ta, amy

---

### Post by sandyd on 2010-01-01
> **AmyB said:**
> Hi all, 

i have done the upgrade from 7.10 to 8.04 via the upgrade system, not the CD install. I am struggling with the sound and playing DVD's.

I have been working on this Dell inspiron 1525 for a few weeks now as this is the first clean install that i could get to work as there has been numerous issues.

I have tried to read as many posts as i could but i still am struggling. I did read another post that was very helpful for the lack of sound issue, adding the ppa etc. however i got as far as loading 2 of the 3 available files, the 3rd, the hsfmodem, is refusing to load. the message i recieve is:
E: hsfmodem-base-dkms: subprocess post-installation script returned error exit status 7

If i look at the detail it says that: The directory /lib/modules/2.64..2-61-generic does not exist, and it cannot load onto a non existent kernal.

i am now lost with this issue!

the second issue is when a DVD is loaded i asked it to chose the codecs for the DVD (i have tried many different DVD's at this point) and it goes to find them, adds them, it all looks ok, then when it goes to play it says:

Failed to connect to stream - invalid Argument

that is the message i get for all DVD's that i try and play.

In general i am a newby to ubuntu, and laptops, but pc's in general i know (sadly windows based platforms are all i learned) so as a favour to a friend of mine i am trying to sort out his laptop for him, and learing ubuntu along the way (he knows nothing at all about pc's)

I refuse to let this get the better of me, but i am thinking that i might need to just do a CD install as was suggested in another post as opposed to working through all of the errors that i am facing (my preferred method is to work through them as i want to learn the workarounds), but after 2 weeks i am ready to cry, scream, chuck the laptop out the window. i dont care what order it happens in. 

the laptop had onboard sound that is enabled (i checked the bios before i did anything else) 

can anyone suggest something or let me know what i might have inadvertently done wrong?

is the fresh CD install the best option at this point?

thanks in advance for the advice, and sorry for the exceedingly long post :)

ta, amy

you need to install the [[linux-headers-generic]]("apt://linux-headers-generic") package in addition to the [[linux-generic]]("apt://linux-generic") package and the [[linux-source]]("apt://linux-source") package (just click on the name of the packages that i just specified in this post to install)

p.s. 9.10 (the latest version) has more hardware support. you can also try that

p.s. it **is **an upgrade problem. that is, accodring to
[http://en.community.dell.com/wikis/linux/ubuntu-8-04-known-issues.aspx](http://en.community.dell.com/wikis/linux/ubuntu-8-04-known-issues.aspx)

p.p.s i was looking around and found that dell has their own iso images. that includes all the drivers and everything :D
their avaalible here [http://linux.dell.com/files/ubuntu/](http://linux.dell.com/files/ubuntu/)
the karmic isos arent generated yet, but you can simply use the jaunty isos and upgrade from there.

---

### Post by Methuselah on 2010-01-01
Firstly, on the sound issue, did you check that your volume is not muted or turned down too low?
This is a simple thing that can sometimes happen.

There should be a speaker panel icon in the upper right that you can double-click for volume settings.
Make sure that 'master' and 'PCM' are not muted or turned down too low.

---

### Post by AmyB on 2010-01-02
Thanks, i will try the dell link, i did check the mute issue etc as i read in another post that could be a problem, but the sound icon was not even present anymore when i did the upgrade but i checked the sound in every other place, including on the laptop itself (it has an external volume button) and oddly if you wanted to change the volume it would pull up the volume tool but you couldnt do anything with it. sigh.

thank you so much for the help, very appreciative :)

---

