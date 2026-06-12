---
title: "Alternate cd"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by ZefQ on 2008-12-04
So i decided to install the "Alternate Cd" to checkout LTSP-alternative, anyway i downloaded, it burned it (i always burn in lowest speed 2.4x) and popped it in. it did not but from cd so my original "ubuntu desktop" started up.

i tried to bur it again in case something went wrong, same thing.
so i decided to download it from an other location, long story short i have downloaded it from 5 different location and still wont boot.

i guess i should have checked md5 but if i haven't been able to get the correct version after so many downloads...

so i don't know anything how CD-boot really works, but i found that non of the CD's had a autorun.inf, i know that the "ubuntu desktop" CD has it. so should it still be able to boot from CD? And if so any tips?

//kempe

---

### Post by Michael.Godawski on 2008-12-04
Make sure:
1.) you have burnt the CD correctly ( I am not patronizing you, just make 100% sure )
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

2.) check your BIOS setup if the CD-ROM is set as the first booting devices.
You get into the BIOS, when you hit esc or f12 or your key combinations which is displayed just after the restart of you machine.

---

### Post by stefangr1 on 2008-12-04
Are sure that your bios-settings are such that your pc tries to boot from cd/dvd first? You can ususally enter the bios by pushing DEL or F2 at bootup. 

Otherwise a bad dvd is the logical explanation.

---

### Post by gjoellee on 2008-12-04
> **stefangr1 said:**
> Are sure that your bios-settings are such that your pc tries to boot from cd/dvd first? You can ususally enter the bios by pushing DEL or F2 at bootup. 
 
Otherwise a bad dvd is the logical explanation.
 
+1 on many computers you have to change some BIOS options

---

### Post by ZefQ on 2008-12-04
for the cd.. i have burnd it maby 10 times so it should not be that. and for the bios, off course i have made sure that it is set on boot cd, if i burn ubuntu desktop or xp it bootes just fine..

---

### Post by stefangr1 on 2008-12-04
> **ZefQ said:**
> for the cd.. i have burnd it maby 10 times so it should not be that. and for the bios, off course i have made sure that it is set on boot cd, if i burn ubuntu desktop or xp it bootes just fine..


Have you already tried to redownload the alternate-cd?

---

### Post by ZefQ on 2008-12-04
oh sorry Michael.Godawski, i did not realize that that was what you meant, I burn it whit nero, "burn image" it has always worked before cant see why it shouldn't work now..

and yeah i i said in the first i have downloaded it from 5 difrent location and the fist 2 locations i downloaded it 2 times

---

### Post by Michael.Godawski on 2008-12-04
Yesterday there was y rather long thread here on this forum dealing with bad md5 checksum of the new intrepid version. If I remember correctly it was the desktop cd 64 bit which did not work.

[http://ubuntuforums.org/showthread.php?t=999051](http://ubuntuforums.org/showthread.php?t=999051)

Perhaps there is really some trouble, but I have no evidence so far and I do not want to put out a rumour.

---

### Post by ZefQ on 2008-12-04
yeah maybe. Should i try the 8.04 alternate version instead?

---

### Post by Malta paul on 2008-12-04
Are you burning using a re-writable CD or a write-only? A re-writable CD dose not burn as deep as a write-only and can give problems with an ISO disk. It is usually better to burning your boot disk using a write-only. ;)

---

### Post by ZefQ on 2008-12-04
Malta paul: yeah i know, sadly i dont have one now, im using rw, but if i burn as I said before xp or "ubuntu desktop" on it it works just fine, i have boot from USB option to and the "ubuntu desktop" USB works fine but not "Alternate CD", i have only tryed "Alternate CD" USB with 2 of the version i have downloaded

---

### Post by philinux on 2008-12-04
> **Malta paul said:**
> Are you burning using a re-writable CD or a write-only? A re-writable CD dose not burn as deep as a write-only and can give problems with an ISO disk. It is usually better to burning your boot disk using a write-only. ;)

I burn all mine on RW's without a problem.

---

### Post by Malta paul on 2008-12-04
Sorry the state the obvious, but after you have downloaded you are burning as an ISO file and not just saving to the CD? ;)
By the way the live CD has a 'disk check item' on the menu to verify your disk.

---

### Post by ZefQ on 2008-12-04
yeah i use nero and the option "burn image". yeah i have seen the live cd option but how would that help me checking the Alternate cd?

---

### Post by Malta paul on 2008-12-04
your are correct it would not help with your alternate CD:confused:

Edit: If you would like me to send you a Alternate CD, send me your address in the private email, good luck.

---

### Post by ZefQ on 2008-12-04
yeah i would like the CD, but shipping cost and things like that, i live in sweden you know...

---

### Post by cmay on 2008-12-04
you can ask for a free cd at the ubuntu home page. they ship it and you just have to wait. you can even ask for more than one so you can give away some to your freinds.  i have also had many problems with getting a good burned iso of the intrepid ibex. i had wasted 6-7 cd before getting one that worked.

---

### Post by ZefQ on 2008-12-04
yeah i checked out the request a free cd now, but shiping 6-10 weeks, man i would have given up this ide and went for something else by then. so i would have a cd that I never would use

---

### Post by Malta paul on 2008-12-04
Shipping from Malta to Sweden is very not much!
Now you have two options to get your CD He! He!
Your choice ;)

---

### Post by theozzlives on 2008-12-04
> **ZefQ said:**
> 
so i don't know anything how CD-boot really works, but i found that non of the CD's had a autorun.inf, i know that the "ubuntu desktop" CD has it. so should it still be able to boot from CD? And if so any tips?

//kempe

The autorun.inf is for Windows

---

### Post by theozzlives on 2008-12-04
Private  message me or go to my website and mail me and I'll e-mail an ISO I know works

---

### Post by ZefQ on 2008-12-04
okey so now i know that that dosen't mather, thought mabye "boot" also needed it. but still cant get it to work. 

one thought, (this is only if my bios or whatever it is that handels cd booting dont suports linux cd boots without autorun, sens whene i try to install os that have autorun on the cd it works)

I have ubuntu installed on the computer i press escape in the boot up chose consol in the boot-meny can i from there maybe start the install. mount cd (thou i dont know how to but it cant be that hard) and run a file on the cd that starts the install?

---

### Post by stefangr1 on 2008-12-04
I think that we can rule out the obvious "bad disk" and "wrong BIOS settings" as possible explanation. This leads to the conclusion that there must be a problem related to your specific hardware in combination with the fact that hardware support on the alternate install cd differs from that on the normal cd. You could probably try your cd on another pc, but I'm sure it would work fine.

Maybe there are some experts on this specific hardware related issues?

I'm not sure for what specific purpose you need the alternate cd, but maybe a workaround is to install the base system from the ubuntu-server-edition, and than the ubuntu-desktop. I suppoze the end result would be equivalent, and it's not so much extra work.

---

### Post by ZefQ on 2008-12-04
I need it to get the LTSP-alternative (Server Terminal) and for thouse of you who want to be nice and tips me about vnc, other things like that and ubuntus own build in alternative. tanx but no, i want to try out LTSP/ubuntu alternative [here]("https://help.ubuntu.com/community/UbuntuLTSP")

but maybe i can use the server version install desktop and from there install the LTSP. But i only have one network-card and if you install with "Alternate CD" it will tell you what you need to do to make it work with one card

---

