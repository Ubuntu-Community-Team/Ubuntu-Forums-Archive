---
title: "Boots to command line, I want it to boot to gui. Among other boot issues"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by JoJerome on 2010-01-10
Just installed Karmic on a Compaq laptop. After lots of initial success...

1) Currently, it boots exclusively to a command line. What command tells it to go to the GUI, is escaping me. Been scouring online manuals and threads for an hour. I'm thinking it's such a simple command it's assumed everyone knows it? Anyway, how do I get back to the desktop and keep it booting to the desktop and not to the terminal?

2) How do I control what it does or doesn't do when the lid is closed while still powered up? Currently, it causes it to only be able to boot to a grub> prompt and I had to re-teach it how to boot. Found that solution at:
 [https://help.ubuntu.com/community/Grub2#Rescue](https://help.ubuntu.com/community/Grub2#Rescue) Mode

Sorry for the extreme newbie questions ... been a year since I've played in Kubuntu, I do love tinkering in the command line, but have frustratingly forgotten a few of the simple commands. Such as $~ sudo get-me-out-of-here-and-back-to-the-GUI-please.


;)

---

### Post by warfacegod on 2010-01-10
Try: startx

System> Preferences> Power Managment> On AC Power tab and On Battery Power tab> When laptop lid is closed.

You may also have a BIOS setting for that.

---

### Post by richardjennings on 2010-01-10
1) Look for the word "single" on the kernel line of the option you select to boot with grub. If it is there, removing it will prevent grub from booting ubuntu in single user mode.

---

### Post by JoJerome on 2010-01-10
Thanks, though sadly ...

On 1)  startx tells me "No screens found."
 start kdm also gives me error messages.
 alt+f2-f7 do not work either.

On 2) Can't look at it now until I get to that desktop screen, but when I looked at it last night:
 No such path System -> Preferences.
 When I follow System Settings -> Display -> Power Control ... the only options I have are to set length of time until suspend, standby, power off. Nothing regarding AC vs Battery power or laptop lid.

RichardJennings- Thank you too. But I don't get any boot options. It acts like it's about to boot to desktop but goes straight to command line.

:(

---

### Post by warfacegod on 2010-01-10
Are you dual booting with wubi by any chance?

---

### Post by JoJerome on 2010-01-10
Nope. Killed Vista completely and installed 9.10 exclusively.

Day of install, all went as expected. Needed to manually tweak the wifi and nVidia drivers, but otherwise all went well. Lots of restarting, turning off and on. No boot problems at all.

I do wonder though... In my quest for video fixes I installed an nVidia package out of the repository which I later figured wasn't the right one/not necessary. It's a long shot, but I wonder if it's causing any issues? I'd go in and check it but .. oh yeah, can't get into the desktop! Grrrrr....

Thanks again for all the help guys. I'm talking up Ubuntu big-time to my friend here. Hard to do that when I can't get it to boot!

---

### Post by llawwehttam on 2010-01-10
The nvidia drivers from the repos have caused me endless trouble over the years in numerous distros. I always get them from the nvidia website.

You can easily ftp into download.nvidia.com to get the nvidia drivers.

```
llawwehttam@Blackblood:~$ ftp download.nvidia.com
Connected to 32940.ftp.download.akadns.net.
220 spftp/1.0.0000 Server [213.248.114.243]
Name (download.nvidia.com:llawwehttam): guest 
331 Password required for USER.
Password:
230- 
230- ---------------------------------------------------------------------------
230- WARNING:  This is a restricted access system.  If you do not have explicit
230-           permission to access this system, please disconnect immediately!
230 ----------------------------------------------------------------------------
Remote system type is UNIX.
ftp> 

cd to the directory you need then get the driver.


```Username : guest
leave password blank.

Once you have the drivers downloaded follow the instructions to install them.

---

### Post by albert s on 2010-01-10
I had a similar problem when i messed about with my Nvidia settings,
I ended up by re-installing my / folder. 
solved everything and then re-installed the correct Nvidia driver.

---

### Post by llawwehttam on 2010-01-10
> **albert s said:**
> I had a similar problem when i messed about with my Nvidia settings,
I ended up by re-installing my / folder. 
solved everything and then re-installed the correct Nvidia driver.

Don't worry I have done this on numerous occasions.

---

### Post by JoJerome on 2010-01-10
> **albert s said:**
> I had a similar problem when i messed about with my Nvidia settings,
I ended up by re-installing my / folder. 
solved everything and then re-installed the correct Nvidia driver.

As in, messing with nVidia settings caused the boot sector to start hating you? 

If so, where/what is the / folder and how do I reinstall it?

---

### Post by albert s on 2010-01-10
i used my liveCD and started a new install,
but on the guided partition bit i selected manual,
left all partitions as they were, except for the / partition,
ticked the format box and then clicked on install,
re-installed ubuntu with all my data still intact on my /home partition,
be sure to NOT tick the format box for /home.
hope this helps, Im pretty new to all this.

---

### Post by JoJerome on 2010-01-10
> **albert s said:**
> i used my liveCD and started a new install,
but on the guided partition bit i selected manual,
left all partitions as they were, except for the / partition,
ticked the format box and then clicked on install,
re-installed ubuntu with all my data still intact on my /home partition,
be sure to NOT tick the format box for /home.
hope this helps, Im pretty new to all this.

I've heard of this before. Diving into it:

I'm at the manual "Prepare Partitions" step. My partitions are:
```

 _Device           Type         Mount Point         Format?        Size                    Used_           
/dev/sda               
   /dev/sda1        ext4                                                          154651 MB        13436 MB
   /dev/sda5        swap                                                          5387 MB                     0 MB

```

At the bottom, option tabs for New partition table, add, change, delete. 

Are you saying I should only check 'format' under /dev/sda5 since that seems to be the boot partition?

---

### Post by albert s on 2010-01-10
as I said, Im pretty new to all this too,
but I had 3 partitions on my HDD
/
/home
swap
you dont seem to have a separate /home partition
maybe someone else with more experience can help out here.
your swap partition is not your boot partition, its a swap area for RAM when you hibernate AFAIK.

---

### Post by JoJerome on 2010-01-10
Thanks Albert. I hope there's some expert help out there too. If I even knew how to connect the wireless and update any boot logs I need to from the command line, maybe that would do the trick?

Command line seems to work fine. I'd love to just look for and if need be, restore a few init files. If only I knew how to look, and what I'm looking for.

---

### Post by albert s on 2010-01-10
Im fairly sure in UBUNTU at least there is a KILL command available to disable your Nvidia driver and revert back to the rubbish resolution standard GUI,
perhaps this would enable you to get back online and update to more recent drivers.

---

### Post by JoJerome on 2010-01-10
Ok, so what exactly is that kill command so I'm killing the right thing?

And I wonder if 'upgrading' from 9.10 to 9.10 would work? At this point I'm about ready to admit defeat and reinstall but it would be nice if I could do so without losing the data we've already put on it.

Is there a restore function that lets me restore boot settings to default?

- Jo ... on a mission ...

---

### Post by richardjennings on 2010-01-10
Once you have ruled out the "single" boot option, have a look at:

```
dmesg
```

```
cat /var/log/Xorg.0.log
```

```
cat /var/log/Xorg.0.log | grep "Log file:"
``` should show the time the log file was last updated (i.e was X started when you booted up??)

It might be helpful to include some back story.

For example, you were booting to a gui after install right?

If so, what did you do before it stopped working? An update?

---

### Post by albert s on 2010-01-10
like I say, its new to me, and also I use UBUNTU as opposed to your KUBUNTU, so I really wouldnt want to even stagger a guess at the command for you.
do you have any really important data on there? you could use CLONEZILLA to copy the HDD before you do a new install.

---

### Post by richardjennings on 2010-01-10
With regards to killing processes:

to see processes running you can use the ```
top
``` command / program

(press Ctrl c to exit it)



I believe the Nvidia driver runs as a kernel module, so there is no specific process to kill.

To see specific modules use ```
lsmod
```

and to search the output for nvidia, you could use ```
lsmod | grep "^nvidia"
```

this almost certainly not going to help you get back to a gui though :)

---

### Post by JoJerome on 2010-01-10
Thank you again and again guys!

dmesg
 ... Of the more than one screen full of data it pulls up, what is catching my eye is at the bottom of the page:
```

NVRM: API mismatch: the client has the version 190.42, but 
NVRM: this kernel module has the version 185.18.36. Please
NVRM: make sure that this kernel module and all NVIDIA driver
NVRM: components have the same version.

```

And it was indeed the 190.x nVidia driver package I installed that I later discovered wasn't the fix I needed. So it looks like it is the nVidia drivers wreaking havoc?

cat /var/log/xorg.0.log
 ... gives me the error message
"No such file or directory"

As to the actions that led up to this, after my nVidia driver install experiment it was restarting/rebooting just fine. The trigger to all this seems to be when the laptop lid was closed while still powered up. 

Doing that caused it to only be able to boot to a sh grep> prompt. Following the instructions in
[https://help.ubuntu.com/community/Grub2#Rescue](https://help.ubuntu.com/community/Grub2#Rescue) Mode
fixed it. Booted to desktop, and other than the start panel weirdly squishing everything to the left and not showing windows in use, all seemed fine. 

The next time the laptop was shut down, it has since not booted to desktop, only to command prompt.

So it's sounding like whatever I did in the grub rescue woke up the sleeping nVidia bug? 

lsmod | grep "^nvidia"
... I get the message "10316776 0"

I'm guessing that to mean it's not finding the nvidia drivers/processes?

Would it help to find and remove nvidia drivers? Possibly that specific 185.x driver? How would I do that from the command line?

---

### Post by richardjennings on 2010-01-10
> cat /var/log/xorg.0.log


there is a capitalised X

```
cat /var/log/Xorg.0.log
```

anyways you found the error is with the nvidia driver.


At this point I would suggest starting a new topic with a title such as "How do I reinstall the nvidia driver" or to that effect.


I have not done this myself, but I would first try

```
sudo apt-get remove nvidia-glx-185
```

then
(reboot if you like)

```
sudo apt-get install nvidia-glx-185
```

---

### Post by JoJerome on 2010-01-10
RichardJennings - You are my hero.

Just as I was about to hurl the laptop and myself into the Grand Canyon...

Thank you all so much! This definitely won't be my first issue. In fact, the next mystery is the start panel with everything that's supposed to be on the right (time, battery status, etc) squished to the left and windows don't show up in it. 

But at least I'm back in the desktop now and learned a great deal from all of you along the way!



:popcorn:

---

### Post by richardjennings on 2010-01-11
ah cool so reinstalling the nvidia package worked?

---

### Post by richardjennings on 2010-01-11
> In fact, the next mystery is the start panel with everything that's supposed to be on the right (time, battery status, etc) squished to the left and windows don't show up in it.

try:

right click panel / new panel

right click new panel / add to panel

Main menu / add
Notification area / add
windows list / add


If this new panel looks more like what you want, you can right click the old panel and click Delete

---

