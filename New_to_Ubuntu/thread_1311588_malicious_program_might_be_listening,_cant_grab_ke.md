---
title: "malicious program might be listening, cant grab keyboard"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by mrpeachy on 2009-11-02
I just started up ubuntu 9.10.  Everything went fine with the boot, but when it was over i found that i couldnt access anything.  Applications, places and system wouldnt give me drop down menus.

i could start firefox, but i couldnt use the keyboard (after using it to log into my session)

i had a root nautilus launcher on my desktop so i tried to launch that and it gave me a warning along the lines that there could be a malicious program listening to my session and that it couldnt grab my keyboard.

i couldnt shutdown as that drop down was also frozen.

i hard rebooted and now everything os working fine.

is this just ANOTHER 9.10 error, or do i have something to worry about?
and if i have something to worry about, how do i fix it??
if its another problem with 9.10 them i may well just ditch it and go back to 9.04 where i had no problems of this kind at all!

thanks

---

### Post by lavinog on 2009-11-03
It could have been a hardware problem.
The message about a malicious program listening because the session couldn't grab your mouse or keyboard can come up for reasons other than malicious programs...mostly when your computer is overloaded.

If this was right after you installed, I would assume it isn't malicious.

What are your system specs?
Did you check the md5 of the cd after downloading?
Did this happen before performing a system update after the initial install?

---

### Post by dj-toonz on 2009-11-03
Sometimes it also pop's up if you either click somewhere else on screen just at the same time as something is just appearing on the screen and the new thing what's popped up can't get a keyboard or mouse lock. for example I've had it when I pressed a key on the keyboard just before the password box appeared on the screen after opening up update-manager & it couldn't grab keyboard, so in some cases it's nothing to worry about

---

### Post by mrpeachy on 2009-11-03
thanks for the replies!
ive had 9.10 installed for a few days, and i havnt downloaded on installed any unusual packages, and the ones i did were through the software center.

so i dont think it could be an actual malicious attempt to hack my computer.

im running a AMD Athlon(tm) XP 2600+, 1gb ram, 80gb hdd
and i ran the disk check from the live cd before i installed

so looks like nothing to worry about.  and i can assume that the "cant grab keyboard" and the system freeze were just coincidences then?

---

### Post by PC_load_letter on 2010-01-19
This same exact thing that the OP mentioned happened on my Thinkpad running Xubuntu 9.04 after I woke it up from suspension. There a few apps already running (Firefox, Thunderbird), with 1.5 GB RAM I don't think it was a memory issue. 
In any case how would one spot a malicious eavesdropping process working in the background?

---

### Post by webdevelopment on 2010-02-15
i had this happen to me right after it told me that some DSA key couldnt be verified...

never seen this before...  

it said someone could be eaves droppping?

---

### Post by PC_load_letter on 2010-02-16
That's exactly what happened to me and it scared the $#it out of me. I gooogled and I found a reasonable explanation that it's somehow has something to do with the battery recharging. So I suggest that you try your laptop without the battery installed and see if you get the same thing.

---

### Post by Richard1979 on 2010-02-16
> **PC_load_letter said:**
> This same exact thing that the OP mentioned happened on my Thinkpad running Xubuntu 9.04 after I woke it up from suspension. There a few apps already running (Firefox, Thunderbird), with 1.5 GB RAM I don't think it was a memory issue. 
In any case how would one spot a malicious eavesdropping process working in the background?

Open System > Admin > System Monitor and look at the Processes tab.
Viruses are virtually impossible to hide under Linux and if something nasty is running, it will be listed in there (assuming you didn't enter the admin password when not performing admin tasks).
Bear in mind that most of the processes (or all most likely) in that list will be legit.

---

### Post by lavinog on 2010-02-16
htop is a little easier to read
or 
```

ps -ef

```

---

### Post by webdevelopment on 2010-02-23
a virus could be renamed as apache or some system filename

but how do I know what all the system process are and if one is a virus without a list to reference?

---

### Post by lavinog on 2010-02-24
> **webdevelopment said:**
> a virus could be renamed as apache or some system filename

but how do I know what all the system process are and if one is a virus without a list to reference?

Apache should not have root access.

You could post them on the forums, but you could be wasting your time.
If the malicious program came from ubuntu's repository, you may not have any easy way to determine if it is.

You could use netstat or a network sniffer to see if a program tries to phone home.

---

### Post by PC_load_letter on 2010-02-26
> **lavinog said:**
> Apache should not have root access.

You could post them on the forums, but you could be wasting your time.
If the malicious program came from ubuntu's repository, you may not have any easy way to determine if it is.

You could use netstat or a network sniffer to see if a program tries to phone home.

Stupid question: How do you get htop to output to a text file? Tried it ($htop > processes.txt) but there are many non letter symbols and it looked messed up.

---

### Post by lavinog on 2010-02-26
> **PC_load_letter said:**
> Stupid question: How do you get htop to output to a text file? Tried it ($htop > processes.txt) but there are many non letter symbols and it looked messed up.

you should use this instead:
```

ps aux > processes.txt

```

---

### Post by PC_load_letter on 2010-02-28
> **lavinog said:**
> you should use this instead:
```

ps aux > processes.txt

```

Thanks a lot!

---

### Post by sethsn on 2011-02-19
Hi
 
I've started getting the very similar behavior (can't grab mouse instead of keyboard) since running update manager yesterday.  I'm running x64 10.04 LTS - The Lucid Lynx - on a 2.66GHz Core2 Quad with 8Gb of RAM, Gigbyte EP45-UD3L mobo, Gigabyte GV-R4350C-512I graphics card and SATA disks.  The problem is compounded by something grabbing most mouse events and preventing me from switching focus between windows.  The mouse moves and the keyboard works but that's about it.  I've tried selectively killing X clients but have yet to track down the culprit.  xlsclients is your friend.
 
Any help gratefully received
 
Nick

---

