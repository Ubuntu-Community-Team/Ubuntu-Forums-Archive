---
title: "Remove virus on infected PC"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by sunwatt on 2009-07-01
My Dell Insperon 9100 laptop (XP) has WiniBlue and its locked up. This is a very bad one.

The HDD is 100GB, and everything important is backed up.

How do I get my Ubuntu 9.04 live DVD to scan and remove the virus?

I'm on adsl and none of the live DVD's allow me to connect to the internet.

This video is close to getting me there, but she skips over the part I need help with.

[http://www.youtube.com/watch?v=9h3q5ss40oY&feature=related](http://www.youtube.com/watch?v=9h3q5ss40oY&feature=related)

If I cant get rid of the virus I'll just install Ubuntu and wipe the HDD and my XP will be gone. Cant find my XP reinstall CD.

But in case the XP can be cleaned, and still is intact, I'd sort of want it around.

Thanks!

Jim

---

### Post by tarps87 on 2009-07-01
How do you connect to the network/internet? i.e. wired/wireless/dial-up

If you are looking for a virus scanner I would recommend clamav.

Before you do too much I would recommend making a back up of the data if you have any form of backup medium, if you want to do this and need any help just post back

---

### Post by sunwatt on 2009-07-01
I'm wired via Ethernet cable to my adsl modem. In that video she uses the built in virus scanner already on Ubuntu 9.04   that would be easier for me I think

Everything is already backed up

---

### Post by tarps87 on 2009-07-01
I've not noticed a built in virus scanner, could you post a link to the video and I'll have a look when I get home. (Just interested)

As for the internet connection, I believe all the information you need can be found here:
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
I have never tryed setting up a DSl/ADSL connection, but if you have any problem just post back and if I can't work it out I'm sure someone else can.

Other than that you seem well prepared

---

### Post by sunwatt on 2009-07-01
Thanks, I edited my post, the youtube link is there now. This video says you can use Ubunti 9.04 live cd on an infected pc. Boot up to cdrom and maybe you have to import the virus scanner.

Maybe she said, you can do a virus scan even if no internet, but there is something she mentions, and skips over it

I'll look at your link and try to connect again

thanks

---

### Post by tarps87 on 2009-07-01
Thanks, It had to be utube :) It is blocked from work so I will look when I get home and see if I can be of any help

---

### Post by jrandolph on 2009-07-01
So im just butting in here and wondering if everything important is already backed why not just wipe the whole hd and start with a new 9.04 intall? If all you want to do is remove a virus and start over surely wiping the hd would get rid of it and give you a nice new hd to start with.

---

### Post by sunwatt on 2009-07-01
Thanks! I looked at the link you gave me on adslpppoe. As I am using a CD, and Ubuntu is not installed on the PC Im using, or the infected PC, I think I'll need to follow the Manual connection control, at the terminal I type   pon dsl-provider

As I am very GREEN with all this the Terminal commands are very new to me, and Ive never really used DOS before, so Im feeling my way along.

With the live CD Ubuntu all changes I make are lost once I leave Ubuntu, so the manual adsl pppoe might be best?

I'll try it, and if I get online, I'll try and follow what the youtube video says. Its a little hard to follow, and like I said she mentions how to run import and run the AV to get a virus, but she skips how to do it, and assumes you can get online.


I'm just learning Ubuntu, my Dell Mini 10V shud arrive next week.

But I have these 2 Dell insperion 9100 laptops, this one is virus free, but only a 30gb hdd, and a fan issue. 

The 9100 with the 100gb hdd has the winiblue virus, and I want Ubuntu on it. If I can save the XP, I'd have it be dual boot.

The Dell 9100 is 2004, not sure if Ubuntu 9.04 is the best fit, I was told I might have to resort to Knoppix 5 or 6 - But I'll try Ubuntu 9.04 and see__

---

### Post by sunwatt on 2009-07-01
Thanks for asking... Im on the edge of doing just that, wiping the HDD clean. However, if I could have XP in case I ever need it again, I'd like to save it if I can.

Its worth one try with the Ubuntu AV scan I think.

Trust me, I hate XP more than ever now, I might let it go if this AV scan gives me much trouble.

:)

I'm gunna reboot with the 9.04 DVD and try the manual adsl pppoe config, be back soon

Thanks!!!

---

### Post by sdbrogan on 2009-07-01
Here is a ClamAV live CD (based on a slimmed-down Ubuntu) :

[http://www.volatileminds.net/projects/clamav/](http://www.volatileminds.net/projects/clamav/)

The virus definitions are updated hourly so it shouldn't matter that you can't connect to the internet on the infected PC.

If your XP installation disc turns up you might want to think about running it on a virtual machine within Ubuntu - that way re-installing it (together with all your settings & installed programs) becomes a simple cut & paste.

---

### Post by khelben1979 on 2009-07-01
If you boot up an installed Linux system from another harddrive, then you can always try to remove the viruses by running the anti-viruses through Wine. I don't know if it works, though.

[List of computer viruses]("http://en.wikipedia.org/wiki/List_of_computer_viruses") and [list of anti-virus software]("http://en.wikipedia.org/wiki/List_of_antivirus_software") - Wikipedia.

Good luck!

---

### Post by tarps87 on 2009-07-01
pppoeconf is installed on 9.04 by default so the manual setup should work, if there are problems connecting to the internet sdbrogans' suggestion might not be a bad idea.
Just thinking if your xp install can not be fix you should be able to get a recovery cd form the manufacturer or failing that there should be a cd code on the case somewhere then you will just need a xp cd

---

### Post by sunwatt on 2009-07-01
Thanks, its downloading ClamAV right now, I'll let you know what happens.

---

### Post by sunwatt on 2009-07-01
Ok, I burned the bootable CD clamav, it loaded, and I hit enter to take me to the graphical interface. The top selection was highlighted, to run clamav so hit enter.

It loaded some more, and took me to ubuntu@ubuntu:~$  I typed in fdisk -1 as it said in the titorial and it says fdisk: invalid option -- 1

below that is a bunch of stuff... Usage: fdisk [-b SSZ]  [-U] DISK     Change partition table
fdisk -1 [-b SSZ]  [-u] DISK    List partitiotion table (s)

On and on

I am having trouble using the ClamAV

Jim

---

### Post by carml on 2009-07-01
The command id fdisk -l it's a lower case L not a 1 ( number one ),that's a common mistake ;).

---

### Post by sunwatt on 2009-07-01
OK, no more fighting this... Ubuntu 9.04 is installing now 22%, hope my sound and everything works

thanks!

---

### Post by carml on 2009-07-01
Welcome on board ;)

---

### Post by sunwatt on 2009-07-01
Thanks to ALL of you... Screw the virus, I just installed 9.04 on top of XP I guess.

I'm online, and using Ubuntu that I just now installed.

Allot of work ahead, making sure music plays, youtube working, and such. I have bookmarks from my Firefox I need to import.

But this is a labor of love.

Next week my Dell Mini 10V will arrive.

Does it get any better?

better not speak too soon, this 2004 laptop (Dell Inspiron 9100) may have some issues....  

But no more virus!!!

If I have issues can I post here? or move to another part of this forum?

Jim

---

### Post by bodhi.zazen on 2009-07-01
> **sunwatt said:**
>  But this is a labor of love.

Next week my Dell Mini 10V will arrive.

Does it get any better?

Jim

How long did it take you to learn to do all that  on Windows ?

I find it takes 3-6 months to learn a new OS so as long as you are willing to learn you should have no problem.

Ubuntu strives to be a distro for new users, many people come for the OS and stay for the community.

---

### Post by xeticus on 2009-07-01
Sunwatt like you I'm a new Ubuntu user from XP.  The hardest thing for me was getting DVD's to play, getting Compiz installed for all the awesome graphics and I still can't get my wireless to work(haven't tried too hard) but for most things my Ubuntu just works faster and easier than my Windows XP ever did. I think 9.04 was the right time for you to make this move. It's the first time I thought linux seemed actually superior to windows for a novice. Good luck!!

---

### Post by tarps87 on 2009-07-01
> **sunwatt said:**
> Thanks to ALL of you... Screw the virus, I just installed 9.04 on top of XP I guess.

I'm online, and using Ubuntu that I just now installed.

Allot of work ahead, making sure music plays, youtube working, and such. I have bookmarks from my Firefox I need to import.

But this is a labor of love.

Next week my Dell Mini 10V will arrive.

Does it get any better?

better not speak too soon, this 2004 laptop (Dell Inspiron 9100) may have some issues....  

But no more virus!!!

If I have issues can I post here? or move to another part of this forum?

Jim

I would suggest still posting in this area but in a new thread so that others will the same problem to can find the solution easier.

I had a look at the video and it was basicaly istalling clamav also known as clamtk. Oh and the persion that create the video is also a member of this forum, just as shame see didn't see your thread :)

---

### Post by sunwatt on 2009-07-02
> **carml said:**
> The command id fdisk -l it's a lower case L not a 1 ( number one ),that's a common mistake ;).
Thanks!!! fdisk -l    not fdisk -1   I'll remember that

---

### Post by sunwatt on 2009-07-02
> **bodhi.zazen said:**
> How long did it take you to learn to do all that  on Windows ?

I find it takes 3-6 months to learn a new OS so as long as you are willing to learn you should have no problem.

Ubuntu strives to be a distro for new users, many people come for the OS and stay for the community.
My son reinstalled XP once for me. It took him half a day. So, me? Ive never installed any OS before. That makes me a test case. I'm 62 years old, a great time to learn a new OS, eh?

Yesterday I got skype installed from synaptic, and did a little hacking with the sound settings on skype, and it did a good test with echo123. Got utube working. My mp3's play.

AVI's only play sound, right now. But I'll get some help on a fresh thread and solve that.

This Dell inspiron 9100 is vintage 2004 and its never worked better. Burned a audio CDR yesterday, next I'll try and burn a DVD.

Great fun you'all!

I cant believe it was so simple, just install on top of the infected XP.

Many thanks

Jim

---

