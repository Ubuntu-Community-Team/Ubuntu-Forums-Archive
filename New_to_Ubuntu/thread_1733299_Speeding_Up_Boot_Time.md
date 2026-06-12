---
title: "Speeding Up Boot Time?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Chrissd on 2011-04-19
Hi,

At University, the amount of time it takes for my little Notebook to boot feels a long time. It's an Acer Aspire D255 with 1.5GHz. 1MB L2 cache, 1GB of RAM (I'm reading the sticker on the case :D ). I'm using Xubuntu, as I understand it's the lightest official version of Ubuntu.

Can anyone direct me to areas where I might be able to speed up the boot time at all, if it's at all possible? I found a thread, but it's 6 years old and I'm certain many things have changed since then.

---

### Post by mastablasta on 2011-04-19
you didn't post your graphics card and disk size.
 
It shouldn't feel a long time if everything is installed and configured propperly. It should boot in about 15-20 seconds.
 
you know you could easilly run Ubuntu on that setup.
 
edit: when you log in you can choose Xubuntu or even lighter one called Xfce Session. ;-)

---

### Post by kerry_s on 2011-04-19
Have you tried suspend?  Saves alot of boot time.
modern kernels are much bigger than they use to be, long boots are the result.

---

### Post by Chrissd on 2011-04-19
This partition has around 200GB or so, and my Graphics card is a
```

Intel Corporation N10 Family Integrated Graphics Controller (rev 02)

```

I say boot, I mean from end of the Grub selection screen to me being able to use it is around 1 minute, not including the time to type my password in.

Can you tell me the difference between XUbuntu and XFCE?

---

### Post by Chrissd on 2011-04-19
I do use suspend between lectures/seminars, however, it's the initial boot of the day that drags on.

Perhaps I'm just impatient, but anything that would save even a few seconds would be useful.

---

### Post by jtarin on 2011-04-19
Look in "dmesg" and see what services are starting and what services you can eliminate.

---

### Post by fabricator4 on 2011-04-19
> **Chrissd said:**
> Hi,

Can anyone direct me to areas where I might be able to speed up the boot time at all, if it's at all possible? I found a thread, but it's 6 years old and I'm certain many things have changed since then.

I found I was able to significantly speed up the boot time on my EeePC by stopping any unnecessary programs from starting up.  Things like ssh and Ubuntu One were unnecessary (to me) and paring it down to the basics lets the system boot in about 15-20 seconds.  Not bad for a 900MHz Celeron.  I kind of slowed the system down a bit when I changed my /home to the 8GB SD card which is a shame, but having everything running off the 8 GB SDD was just too restrictive. (When I'm feeling clever I might investigate having /home/username on the SSD so it reads config files quickly, but have the rest of the data directories on the SD card but still mounting under /home/username)

I'm afraid I don't know where Xubuntu lets you change what is run at startup, but in Ubuntu it's under startup applications in preferences.

Chris.

---

### Post by mastablasta on 2011-04-19
> **Chrissd said:**
> This partition has around 200GB or so, and my Graphics card is a
```

Intel Corporation N10 Family Integrated Graphics Controller (rev 02)

```
 
I say boot, I mean from end of the Grub selection screen to me being able to use it is around 1 minute, not including the time to type my password in.

1 minute does seem a bit long (laptorp 1,2Ghz, 224MB ram and it boots in about a minute in ubuntu). as mentioned dmesg should show you any errors. IT is probably trying to mount something and failing or succeede in a couple of tries.
 
> 
Can you tell me the difference between XUbuntu and XFCE?
 
 XFCE session is more bland. try it out, you can easilly switch back later on. you will see. it looks more like Win98 or Linux from the 90's :-D
 
ok to reduce RAM usage another trick (besides already mentioned) is to reduce number of virtual desktops. I mean if you are not using them then why have so many? also sometimes wallpaper can take RAM as well as time to load. try without it.

---

### Post by Chrissd on 2011-04-19
Ok, so far I've stopped things I know I can safely stop in startup, I've stopped a few of the tty things from starting too (now have two) and turned the other virtual desktop. Also turned the splash screen off. Wallpaper is solid black.

From Grub selection screen to being usable is 1 minute exactly (actually, take a few seconds off to type my password).

What am I looking for in dmesg? Would my encrypted home directory slow things down significantly?

---

### Post by Chrissd on 2011-04-19
Fwiw, I've just changed to XFCE rather than Xubuntu Desktop, and loving the retro feel. :guitar:

---

### Post by mikewhatever on 2011-04-19
> **Chrissd said:**
> ...

What am I looking for in dmesg? Would my encrypted home directory slow things down significantly?

Look for large gaps in timestamps. The encrypted home probably doesn't help speed things up, but really, a minute to boot is not a big deal, at least IMHO.

---

### Post by Locke_99GS on 2011-04-19
There are other DE/WM's available that are lighter than XFCE. LXDE (Lubuntu) is full featured and much lighter on resources. As mentioned, remove anything you don't require.

Using a smaller, leaner kernel can help, as can newer kernels. Kernel code is being optimized in every version, and sometimes new features are implemented which can improve your experience. For instance, the 2.6.38 kernel fully implements autogroups (the 200-line cgroups patch, improved) out of box, which is kinda beneficial. (I personally prefer BFS) The Zen kernel patches and configs can make everything quicker also, from a speedier boot to improved response on the desktop and disk r/w.

---

### Post by josephmills on 2011-04-19
> **jtarin said:**
> look in "dmesg" and see what services are starting and what services you can eliminate.

+1

---

### Post by mikechant on 2011-04-19
I haven't used it myself (because my boot times are already about 20-30s) but Bootchart is supposed to be an easy way of seeing what's going on at startup.

[http://packages.ubuntu.com/lucid/bootchart](http://packages.ubuntu.com/lucid/bootchart)
[http://www.webupd8.org/2009/04/ubuntu-boot-chart-make-graph-with-your.html](http://www.webupd8.org/2009/04/ubuntu-boot-chart-make-graph-with-your.html)

---

### Post by Chrissd on 2011-04-20
I'll give bootchart a go. dmesg is a little confusing for me.

---

### Post by lithopsian on 2011-04-20
dmesg is almost useless for this.  It shows what the kernel does in about the first second, and then one or two messages after you've booted.  It *doesn't* show you each service that you start.  Unfortunately most of these services don't get logged anywhere, so people usually turn to bootchart to give them a view of what it starting and how long it takes.

A minute sounds a bit long even for a full Ubuntu install on your somewhat old machine.  Install bootchart, get a graph and then post it here.  Don't post as an attachment or we'll get a tiny image with text less than a pixel high.  You'll have to upload to a hosting site and post the thumbnail here.

Running with the splash screen off is useful for troubleshooting but having it on doesn't really slow things down much.  Also remove quiet from your boot options and you'll see messages as each service starts.  If you can read fast. or if it boots very slowly, you'll get an idea what is taking all the time.

XFCE is pretty cool.  I prefer it to the full Metacity desktop.  You can also try Openbox, even more minimal.

---

### Post by bullgates on 2011-04-30
Hello, I'm also speeding up my htpc (used mainly for xbmc and google chrome for browsing the internet), and I could get good speedups by removing unwanted services as already told, additionally:
- adding the option "startpar" in /etc/init.d/rc
- adding ureadaheah (sudo apt-get install ureadahead), the first startup will be slower but the others will be faster
- since it is a fixed desktop, I've also used a fixed IP instead of DHCP.
- I've also added opendns and google dns as the dns servers instead of my ISP (usually they are really fast)
- adding autologon to any graphic display manager you have, or by completely disabling it (who needs that on an HTPC anyway?)

I maybe missed something but in general this will speed up your xubuntu/ubuntu experience, I will add more tips if I recall of them :)

---

### Post by jtarin on 2011-04-30
> **lithopsian said:**
> dmesg is almost useless for this.  It shows what the kernel does in about the first second, and then one or two messages after you've booted.  It *doesn't* show you each service that you start.  Unfortunately most of these services don't get logged anywhere, so people usually turn to bootchart to give them a view of what it starting and how long it takes.

A minute sounds a bit long even for a full Ubuntu install on your somewhat old machine.  Install bootchart, get a graph and then post it here.  Don't post as an attachment or we'll get a tiny image with text less than a pixel high.  You'll have to upload to a hosting site and post the thumbnail here.

Running with the splash screen off is useful for troubleshooting but having it on doesn't really slow things down much.  Also remove quiet from your boot options and you'll see messages as each service starts.  If you can read fast. or if it boots very slowly, you'll get an idea what is taking all the time.

XFCE is pretty cool.  I prefer it to the full Metacity desktop.  You can also try Openbox, even more minimal.

[Boot-Up Manager ]("http://www.marzocca.net/linux/bum.html")is a Perl-Gtk2 application to handle runlevels configuration of any debian derivative system. With this program the user will easily start and stop boot-up scripts, without the necessity to handle thru complex links and permissions.

Boot-Up Manager has been developed and tested on Ubuntu, but as it only relies on Perl-Gtk2 libraries, it can be run on any Debian-like system.

---

### Post by Chrissd on 2011-05-02
Just installed Boot-Up Manager, looks good! 

Lots of stuff listed there, though, not much ticked. Any good place to find out what stuff I can further untick?

Thanks

---

### Post by lord flasheart on 2011-08-14
> **Chrissd said:**
> Just installed Boot-Up Manager, looks good! 

Lots of stuff listed there, though, not much ticked. Any good place to find out what stuff I can further untick?

Thanks

I have everything disabled but gdm, kerneloops, network-manager and acpi-support

I'm using an aspire one with 1g memory. after various tinkering I've got my boot time down to 30 seconds from at the very least 40. I suggest changing your memswap value as this improved boot time for me noticeably as well as speeding everything else up in general.

---

