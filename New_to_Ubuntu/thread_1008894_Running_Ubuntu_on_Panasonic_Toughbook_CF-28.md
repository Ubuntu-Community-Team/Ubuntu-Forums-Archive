---
title: "Running Ubuntu on Panasonic Toughbook CF-28"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by uwave on 2008-12-12
Just wondering
Has anyone been successful on getting Ubuntu or Kubuntu to run on a 
Panasonic Toughbook CF-28 PIII 1ghz laptop.
I have tried to get 3 of them working dual boot but no joy.
I first tried out the LiveCD's and all I get is a blank flashing screen
every few seconds after the battery check..
Sometimes theres an "X" in the middle of the screen.
After that the system is frozen and I must pull the power and battery to reboot.
Is this just a problem with the new release? 
Do I need to use a previous release?
The CD's work just fine on two of our desktops and I am enjoying 8.10
on them but would really like to get these Toughbooks to run Ubuntu.

I have also loaded up an HP nc6000 with Ub 8.10 and it works fine too.

Thanks

---

### Post by nhasian on 2008-12-12
Please use the Alternate CD text based installer instead of the LiveCD.  that should get you up and running.

---

### Post by uwave on 2008-12-12
Thanks nhasian
I just downloaded the alt version thinking that might work.
Gunna try it out a bit later.

Chuck

---

### Post by uwave on 2008-12-12
Well, I tried out the ALT distro today and I'm still baffled.
At least now the screen is not a flashing black "x" screen.
And now it will get passed the login but it stops with a busy curser
on top of a full brown screen.
Nothing I do will make a change or progression.

The text type install wasnt too bad just took a it longer than I expected.
I had to remove power to get the laptop to shutdown to reboot.
One thing I did notice after the initial install (first reboot) 
I did get the Ubuntu opening audio sound then the brown screen with the busy curser,  but subsequent reboots this did not happen. 
Just the brown screen as stated above.

I have been reading a lot of my original problem on the board today and
I am wondering if I just should try an earlier program.
If I do, Can I just install over the new (bad) one?
I do have copies of 8.04 and its ALT.

I'm about to give up on getting Ubuntu into these toughbooks 
Altho it seems like a lot of bother, I did expect problems after I tried the first time and scowered the forum for answers.
I can still choose in the grub menu after reboot.
XP still works fine.

Any Ideas?

---

### Post by SamNSane on 2008-12-12
Let me stress that I am in no way familiar with the Toughbook you are using. I have just been looking for people having issues with Panasonic subnotebooks, so it was the "Panasonic" that drew me to your thread.

I have a Panasonic CF-R3 which had terrible power management problems in 8.10. It has no problems at all in 8.04.1. I posted about it here in the Ubuntu forums and received a response from another person with a Panasonic CF-R4 who was having the same problems. I posted a bug on launchpad which got zero activity in the span of a month. (The normal time allowed is 15 days of inactivity, but I renewed it once.) Apparently, there are few users of these subnotebooks (not made for use outside Japan but brought to USA by dynamism.com) trying to run anything but Windows on them. Apparently, also, such a small number of users isn't going to attract the attention of the admittedly overworked devs who deal with bugs.

Maybe Panasonic customizes something in the BIOS's power management features that doesn't get along with something in Intrepid. This is a tiny, light notebook with a brilliant 1024x768 screen and a decent keyboard (as tiny Japanese keyboards go). It runs 10-12 hours on a charge, so the power management may be aggressive.

Anyway -- more to the point -- maybe you are correct in thinking that taking a shot at 8.04.1 is the thing to do. You are mostly concerned with what sound like video issues, but there most certainly appears to be a possibility of a power management issue with your system in Intrepid, too.

Good luck!

---

### Post by musicalwoods on 2009-03-31
Yeah, my CF-28 does not like 8.10 or the 9.04 beta. It works fine in 8.04.02, though.

The erros I was recieving in 8.10 weren't the ones you appear to be having. Mine would look fine, but would not resume from sleep and text would begin to artifact/misprint (look wrong or not display). It's a shame, because I like some of the improvements in 8.10 and 9.04...

---

### Post by spcwingo on 2009-03-31
I just installed Hardy to a CF-72 for my mother-in-law.  It's a P3 model also.  I think it uses most of the same hardware as the CF-28, just in a semi-rugged case as opposed to the full rugged.  I also had problems getting Intrepid to install, so I just threw on Hardy...no problems with the live CD or install process.  If I were in your position I would give Hardy a shot.

---

