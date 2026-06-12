---
title: "Help! Stuck at the login screen"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by frontline2010 on 2010-02-24
This Is driving me NUTZ!!!
When ever it goes to the log on screen it ask for my password so I put it in and it acts like it wants to load up then the screen flashes and goes back to the same log in screen asking me for my password again? So after fighting with it for hours and trying to find info on how to get pass this I gave up and tried to reinstall Ubuntu but this time I told it to automatically log in instead of putting in a password and that work fine for a week ....but this morning I got up and moved the mouse &#8220;to wake up the screen saver&#8221; and the desktop came up and then for no reason at all jumped to the log in screen asking for my password!!! So I put it in &#8220;Praying to god it will let me in,&#8221; but no..it locks me out again!!! I tried to restart it and **BAM!!** there is the log in screen that wont let me in...What upsets me is the fact that I did NOT give Ubuntu permission to use the log in screen at all and just like Windows Ubuntu dose what it wants when it wants to without the owners permission. What I&#8217;m asking is there some way to fix this so that I can recover my files?I admit that I am new to the whole Linux Ubuntu operation system but I&#8217;m pretty savvy when it comes to most other OS...So why it keeps doing this is truly beyond me and kind of sad I really really wanted to give Ubuntu a chance:confused: 

The PC I am using is Compaq Presario SR1030NX

---

### Post by spiderbatdad on 2010-02-24
Sorry you are having this problem. Obviously it is not normal, or we would all be just as upset.
This type of problem can be tricky to diagnose. I have seen some info on google regarding Ubuntu login loops for other users on specific machines...that might help if you can find anything solved.
Other times, certain hardware requires parameters to be passed to the kernel at boot time, like acpi=off, or noapic pci=routeirq.
To find out if this is necessary in your case it might help to see the dmesg file. Run the following command to create a text file on your desktop, then please paste the text file to ubuntu pastebin for review. Be patient for response. [http://paste.ubuntu.com/](http://paste.ubuntu.com/) after pasting your file there, copy a link to your pastebin into another post here.

```
dmesg > ~/Desktop/dmesg.txt
```

---

### Post by MSich on 2010-02-24
I doubt I can help, but it will at least bump it back to the top.
 
Tell me a little more about your installation.
 
Is it dual boot or just Ubuntu?
 
Do you have multiple partitions?
 
Did you set your own partitions or let Ubuntu partition the whole drive?
 
So, right now does it accept the password you defined in the installation?  Even though you selected it to just login, you still had to set an authentication password.
 
Have you tried running just the LiveCD and see if you have problems?
 
Sorry I can't offer more.  Hopefully somone with more knowledge will jump in here.

---

### Post by frontline2010 on 2010-02-24
No it's pretty straight forward clean install nothing funny no dual boot and I let Ubuntu use the whole drive

---

### Post by dondiego2 on 2010-02-24
I had an issue like that when I first installed Ubuntu.  I finally went online and downloaded a new ISO of Ubuntu and burned it to a new disk.  I reinstalled with that disk and have been running fine since.

---

### Post by MSich on 2010-02-24
I just did a search on the forum for "login loop" and it did return some threads.  Including this one  [http://ubuntuforums.org/showthread.php?t=911497&highlight=login+loop](http://ubuntuforums.org/showthread.php?t=911497&highlight=login+loop)  that sounds like what you're describing.  There are some things to try, and the last post may have a solution.  It's worth a read.

---

### Post by oldsoundguy on 2010-02-24
It also could be a video driver issue as after you log in, it will go to the PREFERRED video settings vs the standard VGA on boot up.

Can you boot from the CD and does it run OFF of the CD?

---

### Post by frontline2010 on 2010-02-24
[B]Re: Login screen returns to login screen? 
Hi,

had the same problem last month. In my case, there have been two files in my home directory with root:root ownership (.ICEauthority and .nvidia-settings-rc). Just changed ownership and everything is back to normal.

Hope this helps and greetings.[/B]





OK thats the one I will give a try .........How ever......I'm a linux nooooooooob How do I change ownership settings to do what this guy said?

---

### Post by AlanR8 on 2010-02-24
Which version of Ubuntu are you using? If Lucid Alpha 2 there are some login issues but loads of easy work arounds!

---

### Post by whoop on 2010-02-24
I've had this problem on one machine once. It would even loop auto-login with the livecd. This was with ubuntu 8.04, I worked around it by using xubuntu, which didn't have the problem. Now the machine is running as a server which never gave me this issue.

I'm sorry that I didn't really found a descent fix for it at that time.

I am also interested to now which version you are using...

---

### Post by frontline2010 on 2010-02-24
I'm not sure.....I downloaded it form this site about 3 months ago so I think it's the latest version

---

### Post by Gone fishing on 2010-02-24
> OK thats the one I will give a try .........How ever......I'm a linux nooooooooob How do I change ownership settings to do what this guy said?

The command you need is chown ```
sudo chown newowner filename
```

I trust you know that alt control F1 will open a console so that you can login

---

### Post by Gone fishing on 2010-02-24
What happens if you start up in recovery mode. Then drop down to a root shell run the command ```
init 5
``` login then the command ```
startx
```?

---

### Post by PPPilot on 2010-02-24
I have the same problem and mine seems to be associated with my video system. I am running Karmic and I have on board S3 video. The S3 driver that was installed by Ubuntu defaults to 1600x1200 at 75HZ. I have a 19 inch monitor but that resolution still makes text way to small so of course I set the resolution down to a more readable level. 

I'm set for auto login but once the resolution is reduced I get the same problem you describe. The monitor clicks multiple times, the splash screen breaks up, and I'm back to the login screen at 1600x1200. For some reason if I power down the machine and restart, it will boot up one time at the lower resolution. This lets me get in and set the resolution back to 1600x1200. I have run my problem through this forum but no answers were found. I have learned to live with the problem by selecting larger type in Gnome and I hit Control + a lot in Thunderbird and Firefox. I thought that one of the kernal updates would help but everyone from 14 thru 19 has not changed anything. So as long as I leave screen resolution at 1600x1200 all is well. I guess to high a resolution is a better problem than others on here who have to low a resolution.

---

### Post by ragskashyap on 2010-10-27
I have the same problem (login looping) Here is my pastebin info

[http://paste.ubuntu.com/520795/](http://paste.ubuntu.com/520795/)

---

