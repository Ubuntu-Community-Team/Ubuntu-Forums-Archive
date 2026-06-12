---
title: "Flash questions, which version &amp; installation"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by ChadBJX on 2009-09-02
Hi,
Total newbie here. I've used windows (since V 3.1 that had to be launched from DOS) for years and have had some Mac OSX experience. I just started this installation around 2pm today. Now it's 4pm and so far I've gotten Ubuntu installed, fumbled around and got my network settings configured so I can get online using my wireless set up. (virtually a no-brainer once I found it :D )

The thing I'm trying to do now is install Flash for Firefox. Not quite sure how to install it. I've gone to the Adobe site and tried a few different options. One download gave an error message that seems to indicate a damaged file. I tried it a few times with the same result. Tried a different version download and can't get that to work either. I'm not even sure which of the versions I should be trying to install.  :confused:

I have Ubuntu 9.04 -the Jaunty Jackalope, installed from the free CD I ordered - if that helps anyone to help me.

I really need to get Flash working and learn how to go about installing other plugins and software.  Some of the instructions at the Adobe site were to go into Terminal and type in commads. Found terminal, can't figure it out. I've downloaded the free PDF book and will study it when I have a chance, but I'd like to get this up and running ASAP.

Thank you very much for any and all help and suggestions.

---

### Post by snowpine on 2009-09-02
Hi Chad! Welcome to Ubuntu. We have a different way of installing software than you may be used to from Windows. Rather than surfing around the internet downloading things, we install from a repository or "repo" of trusted and tested software.

You can do this using the Add/Remove Programs application or the Synaptic Package Manager, but I am going to give you instructions using the terminal (Applications->Accsesories->Terminal) so you can easily cut and paste them.

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

The first line will synch you up with the repository, the second will install the flash player.

It's that easy!

---

### Post by marshmallow1304 on 2009-09-02
Do you have 32-bit or 64-bit Ubuntu?  If you're not sure, go to the terminal and run the command
```
uname -a
```
and post the output.

---

### Post by snowpine on 2009-09-02
ps I forgot to mention that

```
sudo apt-get install ubuntu-restricted-extras
```

will get you lots of other good stuff, like mp3 support and java.

---

### Post by NoaHall on 2009-09-02
If you have 64 bit, download the plug in from the official site - it works much, much faster/better

---

### Post by ChadBJX on 2009-09-02
> **marshmallow1304 said:**
> Do you have 32-bit or 64-bit Ubuntu?  If you're not sure, go to the terminal and run the command
```
uname -a
```and post the output.

This is what terminal returned when I pasted the copied command ...

chad@chad-desktop:~$ uname -a
Linux chad-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux


... does that tell you if it's 32 or 64-bit, and what part of that data tells you which is which?

This is a great forum! Super fast answers!
Thank you very much

---

### Post by NoaHall on 2009-09-02
It's 32 bit, this bit tells you > i686

---

### Post by marshmallow1304 on 2009-09-02
> **ChadBJX said:**
> does that tell you if it's 32 or 64-bit, and what part of that data tells you which is which?

Yes.  As NoaHall said, the i686 tells us that you're running 32-bit.  Knowing this, snowpine's directions should work nicely.

---

### Post by ChadBJX on 2009-09-02
OK, I admit it, I'm a complete idiot here ...

When I pasted the codes, ...

sudo apt-get update   <enter>

this is what I got ...

chad@chad-desktop:~$ sudo apt-get update
[sudo] password for chad: 
Sorry, try again.
[sudo] password for chad: 

... is this my Admin password? And it wouldn't let me type it in anyway

Any way, following the Add/Remove programs clue, I tried that, found Flash and it looked like it installed.

But when I went back to the website I'm trying to use, I no longer get the message that this site requires Flash. But the site does not work correctly. If I can't get that site to work, I'll have to very reluctantly reinstall Win 2000 Pro  

help!!!  :confused:

Latest update, after trying this about 2 dozen times, it finally seemed to work. But the website still doesn't work.  I visited a few other sites with Flash and they seem to work.  Guess I'll have to dig out that Win 2k disk after all.

I'll be able to check the forum tomorrow morning but then I won't be able to work on this computer for several days. :( :confused: ](*,)

---

### Post by snowpine on 2009-09-03
Hi Chad, there is only one password in Ubuntu... it is the password you entered during the install process, the password that you use to log in.

It sounds like the problem with that particular website is not lack of the Flash player. Perhaps you want to post the link so we can take a look?

ps Don't give up and ditch Ubuntu for Windows just because of one website! :) But I certainly encourage you to dual boot Ubuntu/Windows if you need to, lots of us do it... Windows is better for certain things (I use it for iTunes and Netflix).

---

### Post by tomBorgia on 2009-09-03
> **NoaHall said:**
> If you have 64 bit, download the plug in from the official site - it works much, much faster/better

Seconded for 32-bit systems as well!

---

### Post by ChadBJX on 2009-09-03
> **snowpine said:**
> Hi Chad, there is only one password in Ubuntu... it is the password you entered during the install process, the password that you use to log in.

It sounds like the problem with that particular website is not lack of the Flash player. Perhaps you want to post the link so we can take a look?

ps Don't give up and ditch Ubuntu for Windows just because of one website! :) But I certainly encourage you to dual boot Ubuntu/Windows if you need to, lots of us do it... Windows is better for certain things (I use it for iTunes and Netflix).

The problem is, I get out voted. The kids like to play in SmallWorlds.com (the website with the problem).  [http://www.smallworlds.com]("http://www.smallworlds.com/")  The login page won't even load properly.

I've wanted to ditch windows for years. I'd be using my iMac right now if it wasn't in need of repairs, I really want to get a new one but a new computer, of any kind, is not in the budget any time soon.  I'd prefer not to dual boot, I've never had a set up like that before. And in less than 2 days I love how fast Ubuntu runs!!

As I said, I won't have access to this particular computer for several days, but I will be able to get online and read the forum.

In the mean time, here's another newbie question. Why did my Ubuntu CD install the 32 bit instead of the 64 bit version? (probable answer; older computer? If so, what are the system requirements for the 64 bit?)

Thank you,

---

### Post by achase79 on 2009-09-03
make sure swfdec is not installed.  Also put the code below in the address bar in firefox and see what version of flash is installed.
```
about:plugins
```

---

### Post by ChadBJX on 2009-09-03
> **achase79 said:**
> make sure swfdec is not installed.  Also put the code below in the address bar in firefox and see what version of flash is installed.
```
about:plugins
```

In Add/Remove I scrolled through the list of installed programs <all> and couldn't find anything that looked like swfdec, so I'm assuming it's not installed. 

Here's what this says about Flash (I'm guessing you don't want me to copy and paste the entire list.)

**Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Adobe Flash movie swf Yes   application/futuresplash FutureSplash movie spl Yes

And now I really do have to get ready to go to the Dr. and travel across town for several days to help take care of my 84 year old aunt who broke her ankle. <it's my shift lol> And since this "ain't no laptop" I can't haul it with me :(
Thank you

---

### Post by tomBorgia on 2009-09-04
That website loads fine for me - I'm using the adobe flash plugin downloaded from the adobe website -

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

You'll need to completely remove the "flashplugin-nonfree" and/or "swfdec" using synaptic, then use the .deb file downloaded from adobe.com. Its a shame that the non-free / open source flash versions are not 100% compatible...

Hope that helps though!

---

### Post by ChadBJX on 2009-09-05
> **tomBorgia said:**
> That website loads fine for me - I'm using the adobe flash plugin downloaded from the adobe website -

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

You'll need to completely remove the "flashplugin-nonfree" and/or "swfdec" using synaptic, then use the .deb file downloaded from adobe.com. Its a shame that the non-free / open source flash versions are not 100% compatible...

Hope that helps though!

Thank you Tom. I see we are both using the same version of Jackalope. Are you using the 32 bit or 64 bit? Maybe that is making a difference for me. I have the 32 bit, which installed from the CD I got in the mail. So, perhaps the 32 bit is the version that best fits my RAM, processor speed, etc. Also, right now I'm using my uncle's PC (windows) and I'm very new to Ubuntu (about a day and a half of actual hands on before leaving to come help with my aunt. And I won't be back home until Thursday :)) so I'm not really sure how to find synaptic (unless that's the Add/Remove programs application in the menu bar ... I found that pretty quickly.)

I've seen libflashplayer.so at the adobe site but I'm not sure what to do with it once I download it.  I'm guessing that double-clicking it isn't going to work.  Remember; babe in the woods here!!  :confused:

Thank you,

---

### Post by svbh07 on 2009-09-05
> **ChadBJX said:**
> 
In the mean time, here's another newbie question. Why did my Ubuntu CD install the 32 bit instead of the 64 bit version? (probable answer; older computer? If so, what are the system requirements for the 64 bit?)

Thank you,

The CD installed 32 bit Ubuntu because the CD is 32 bit. You have to have a 64 bit CD to install 64 bit Ubuntu.

Try:
```
grep flags /proc/cpuinfo
```

As I just found out over [here,](http://ubuntuforums.org/showpost.php?p=5462561&postcount=9) if "lm" is listed in the output from the above, your CPU is 64 bit.

---

### Post by ChadBJX on 2009-09-10
> **svbh07 said:**
> The CD installed 32 bit Ubuntu because the CD is 32 bit. You have to have a 64 bit CD to install 64 bit Ubuntu.

Try:
```
grep flags /proc/cpuinfo
```As I just found out over [here,]("http://ubuntuforums.org/showpost.php?p=5462561&postcount=9") if "lm" is listed in the output from the above, your CPU is 64 bit.

~$ grep flags /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi **mmx** fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
chad@chad-desktop:~$ 

So, now we know my machine isn't a P4, I knew it was at least a P3. The final question then becomes ... is my computer able to run Flash 10 under Ubuntu? Which is what seems to be needed for that web site.

I'm off to try some of the previous suggestions and to get into reading the free guide book.

Thank you all for your continued help.  :)

---

### Post by ChadBJX on 2009-09-10
I found Synaptic (thanks for that tip) and guess what I found lurking there? Yep, swfdec. Uninstalled it and no more problems.

Thank you, Thank you, Thank you,\\:D/   (happy dance)

---

### Post by reysol48 on 2009-09-11
Want to know what is cause of this white frame affecting this webpage and prevents pull down menu from working 

[ATTACH]128199[/ATTACH]

---

### Post by misfitpierce on 2009-09-11
Unfortunately atm it seems if you got the disc sent from Ubuntu/Canonical you can only get 1 options which auto sends just the 32 bit disc. Why this is like this? I got no idea. It used to have option to get 64 bit or 32 bit which was much preferred and should be re-added. But if you want a 64 bit copy of Ubuntu a CD-R costs no more than $1 and thats super high priced for 1 but you get that, hit ubuntu.com and click amd64/x86_64 and get 64 bit and burn the iso and install.  Easy task and worth the performance enhancment imo.

---

