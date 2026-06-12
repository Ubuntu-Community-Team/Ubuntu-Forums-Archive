---
title: "How to make powertop suggestions permanent?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by mayoban on 2009-05-12
Dear All,

In comparison to Windows Vista (average 4 hours) I only get a maximum of 3 hours battery life from my Lenovo Thinkpad R400 laptop when running Ubuntu 9.04.

As suggested in some other thread, I ran **powertop** to see, if I can reduce energy consumption. These where the the suggestions given:

[LIST]
[*]Enable SATA ALPM link power management via: echo min_power > /sys/class/scsi_host/host0/link_power_management_policy or press the S key.

[*]increase the VM dirty writeback time from 5.00 to 15 seconds with: echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

[*]Enable laptop-mode by executing the following command: echo 5 > /proc/sys/vm/laptop_mode

[*]Enable USB autosuspend by pressing the U key or adding usbcore.autosuspend=1 to the kernel command line in the grub config

[*]Disable 'hal' from polling your cdrom with: hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a window if you plug in a CD but disables SATA power saving from kicking in.
[/LIST]

I understand that powertop changes are confined to the active session. Does anyone know how I could make these changes **permanent**?

Thanks a lot for your help, mayoban

---
I am using Ubuntu 9.04, 64-bit version
on a Lenovo Thinkpad R400, Type 7439-A85
Gnome Desktop with Compiz Window Manager and Cairo-Dock

---

### Post by binbash on 2009-05-12
writing those commands to /etc/rc.local MAY do the trick.

---

### Post by mayoban on 2009-05-13
Hi binbash,

Thanks for your reply. I forgot one important question in the initial post:

How can I make sure, that the changes are **only active**, when the computer is **in battery / laptop mode**?

If I understand the purpose of rc.local correctly, changes would be enabled for **all** sessions.

Cheers, mayoban

---

### Post by djurny on 2009-05-13
take a look in /etc/pm/power.d if you have pm-utils installed..

---

### Post by Axx83 on 2009-05-13
use laptop-mode instead:

[http://ubuntuforums.org/showpost.php?p=7259750&postcount=3]("http://ubuntuforums.org/showpost.php?p=7259750&postcount=3")

---

### Post by mayoban on 2009-05-13
Thanks for the replies!

Re djurny: I checked and I do have pm-utils installed.

Re Axx83: I looked into the post. To me as a Linux beginner, it looks a little bit complicated. Given these instructions, I would not be knowing, what exactly I am doing. Do you know, if there may be a more elaborate explanation out there, or even a GUI for that purpose?

Cheers, mayoban

---

### Post by Axx83 on 2009-05-13
open a terminal
now copy and past what I say and enter after each row

```
sudo gedit /etc/default/acpi-support
```

enter password and then go to the bottom and in the section where it talks about laptop-mode write true instead of false, close document and save of course

```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```

this file is a bit longer, take my attachment as a reference and change what I changed. I added # before the default line on those line I modified, like this:
> #
# Should laptop mode tools add the "noatime" option to the mount options when 
# laptop mode is enabled?
#
#CONTROL_NOATIME=0
CONTROL_NOATIME=1
the default was 0 and I turned it to 1, modify only the lines I modified.
When you're close and save.

```
sudo gedit
```

now in the text editor click open and go into /etc/laptop-mode/conf.d/ folder, there are various files, you probably are interested in usb autosuspend, hda audio, iwl intel wireless, intel sata and sched mc powersaving. Open these files one by one and read them, they're written in a perfect standard english and explain everything very well. You will know what to do, remember that 0 stands for off and 1 for on most of the time.

When you're done close and save each file.

Now restart and admire laptop-mode in action, if you have powertop installed do

```
sudo powertop
```

and examine power consumption, if you've done everything correctly powertop won't have any addition suggestion to make because you've tweaked all there is to tweak (more or less).

Let me know.

---

### Post by Nepherte on 2009-05-13
For graphical applications, use gksu or gksudo instead of sudo.

---

### Post by durand on 2009-05-13
> **Axx83 said:**
> use laptop-mode instead:

[http://ubuntuforums.org/showpost.php?p=7259750&postcount=3]("http://ubuntuforums.org/showpost.php?p=7259750&postcount=3")
Thanks!

mayoban: It is really simple, just read the start of the files and you should get the idea.

---

### Post by mayoban on 2009-05-15
Thanks for all your replies.

Re Axx83: Thanks a lot for your detailed explanation! I think it worked well for me. When in battery mode now, powertop does not give any more suggestions as how to save more power, now power usage is at around 12 watt. 
Powertop estimates the remaining time to be around 4 hours now on full charge. The gnome battery gui is still only estimating 2.45 hours, but I guess it will take some time for it adjust?

Re durand: You are right, the config files really are straightforward.

However, I still think it would still be really great, if all of these features were integrated into the gnome power management GUI, possibly as "advanced settings". What to you think?

---

### Post by durand on 2009-05-15
Of course, that would be perfect and it probably is in development somewhere but there are so many settings that it would be a pretty huge gui. There needs to be some fail safe default options really..

---

### Post by Axx83 on 2009-05-15
> **mayoban said:**
> However, I still think it would still be really great, if all of these features were integrated into the gnome power management GUI, possibly as "advanced settings". What to you think?

Linux has a BIG problem with GUIs but is catching up a little. What is positive is that it's very strong on what matters for real, the backends, let's hope someone will do something regarding laptop-mode and a possible gui.

btw my nb consumes more or less 12w too but my crappy crappy 3 cell battery gives ~2 hours top...

---

### Post by durand on 2009-05-15
> **Axx83 said:**
> Linux has a BIG problem with GUIs but is catching up a little. What is positive is that it's very strong on what matters for real, the backends, let's hope someone will do something regarding laptop-mode and a possible gui.

btw my nb consumes more or less 12w too but my crappy crappy 3 cell battery gives ~2 hours top...

12W? Wow. My 17 inch vostro uses about 25W normally, and tops at 40W when gaming. I wonder if there's any way to make the graphics card use the lowest power level...

---

### Post by Axx83 on 2009-05-15
Mine is a thinkpad x60s with 12" screen and low voltage processor, actually its should go lower than 12w but I guess user manuals do lie sometimes.
AND it costed 1800€ at the time, from my point of view it underperforms...

Regarding your pc, probably the hardware is not very delicate at power consumption, I guess there's not much you can do.

---

### Post by durand on 2009-05-15
Yeah probably not. I run it with the powersave governor almost all the time but it still only has a max battery life of 1:45 hours which is terrible. Bigger batteries cost way too much as well :(

---

### Post by Axx83 on 2009-05-16
You should run it with the ondemand governor not the powersave, the name is misleading since recent studies have proved that letting the cpu throttle up a few times to do tougher tasks consumes less battery than keeping it at minimum, that's because it will take more time to do each thing and stay occupied (but at minimum mghz) more than when ondemand.

Try removing what you did about the governor to ubuntu standards and let me know if it gets better.

---

### Post by mayoban on 2009-05-16
Re GUI: I do not think that a GUI for advanced power management settings using laptop-mode necessarily would have to be huge.

There are 19 config files in /etc/laptop-mode/conf.d/, one for each option. Therefore, the GUI could have 19 checkboxes to enable/disable each of these options (audio, video, hda, sata, wlan, cpu freq control, etc.) and besides each checkbox a dropdown menu if more options could be configured (for example: cpu freq control: on demand, slowest, medium etc.) Plain and simple, and easy to handle for users, who are not familiar with command lines.

So, laptop-mode is a great set of features for powerful and efficient battery conservation. Everything is there, it would only have to be made accessible via a simple GUI: advanced power management options, integrated in gnome power management GUI.

However, I do not know, how much effort it would be to program such a tool.

Cheers, mayoban

---

### Post by kpkeerthi on 2009-05-16
@mayoban
How about suggesting this feature to be implemented in ubuntu tweak?
[http://ubuntu-tweak.com/suggestion]("http://ubuntu-tweak.com/suggestion")

---

### Post by durand on 2009-05-16
> **Axx83 said:**
> You should run it with the ondemand governor not the powersave, the name is misleading since recent studies have proved that letting the cpu throttle up a few times to do tougher tasks consumes less battery than keeping it at minimum, that's because it will take more time to do each thing and stay occupied (but at minimum mghz) more than when ondemand.

Try removing what you did about the governor to ubuntu standards and let me know if it gets better.

I didn't know that! The thing is, I leave it on powersave when playing games because they usually run just as well in powersave mode than when the cpu is maxed out. This also reduces heat so there is a double effect.

---

### Post by Axx83 on 2009-05-17
ondemand has the good effect of both, the cpu stays at minimum and its will stay idle most of the time, when you're on ac there's no reason to keep it at powersave just buy a plastic support to raise the laptop a little and disperse heat.

Trust me.

---

### Post by durand on 2009-05-17
Well, the main reason is that powersave does save power when doing realtime tasks. Since my games run perfectly fast enough in powersave mode, I see no reason to scale up the cpu. Though I do that sometimes when converting music and rendering graphics because it makes sense.

---

### Post by mayoban on 2009-05-17
Re kpkeerthi: Thanks for the info! Up until today I did not know that such a program as ubuntu tweak existed. Adding these advanced power management features is an interesting idea. I will look into the program... And may suggest that.
However, I think, that advanced/improved power management features are so fundamental to laptop users on ubuntu, that they really should be included in a general release. What do you think?

Cheers, mayoban

---

### Post by ibuclaw on 2009-05-17
powertop takes a good share of powersaving tips mostly from [LessWatts.org]("http://www.lesswatts.org/tips/"), so you could pickup a trick or two there.

There are also the odd powersaving tutorial around too. For example: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

Regards
Iain

---

### Post by mayoban on 2009-05-20
Re tinivole: Thanks a lot for your hints! I am sure that Lesswatts.org is a good source for in-depth knowledge on power-saving. The same applies, it seems, to other threads, that you referred to. But I am afraid, I do not have the time to dig into it to a greater extent. In comparison to scripts, the options given by laptop-mode were easily understandable and improved power consumption well.

Cheers, mayoban

---

### Post by mayoban on 2009-05-20
Re Axx83: I had a second look into your laptop-mode.conf.txt file, specifically at the section concerning harddisk control. It reads:

# Power management for HD (hdparm -B values)
#
#BATT_HD_POWERMGMT=1
#LM_AC_HD_POWERMGMT=254
#NOLM_AC_HD_POWERMGMT=254
BATT_HD_POWERMGMT=128
LM_AC_HD_POWERMGMT=255
NOLM_AC_HD_POWERMGMT=255

In some other tutorial I read warnings about how changing these values can **harm the harddrive**, i.e. cause it to break much earlier than normally expected. Could you write a line or two, what these values do exactly? That would be great.

Cheers, mayoban

---

### Post by Axx83 on 2009-05-20
mmm what those line do EXACTLY is way beyond my knowledge. What I know is that those lines I put are exactly the same as Ubuntu standards, since last 2 versions, I guess, Ubuntu turns off powermanagement of hard drives when on ac and put it to 128 on battery. I know that 128 means the disk will never completely park its heads, this to ensure a longer lifespan, but at the same time it is the most you can save of power without parking.

If your hard drive makes A LOT of click noises, make that 128 a 254. The power consumption will be higher but you'll be sure that maximum hard drive life is respected.

Also try 254 instead of 255 for ac, mine prefers 255 but some says that their pc behaves strangely with the 255 parameter. 

By the way I use pc on ac most of the time, on battery with 128 the disk clicks a few times but nothing particular and very silently. Looking at load cycle parameter I can sleep safe for now.

When I have to use windows the drive clicks on ac and on battery.

---

### Post by drorata on 2009-08-21
For me, there are only two files in: /etc/laptop-mode/conf.d/:

* ac97-powersave.conf
* wireless-ipw-power.conf

Where can I find all the other files?

---

### Post by drorata on 2009-08-21
For me, there are only two files in: /etc/laptop-mode/conf.d/:

* ac97-powersave.conf
* wireless-ipw-power.conf

Where can I find all the other files?

---

### Post by Axx83 on 2009-08-21
mmm I have no idea, which version of ubuntu and of laptop-mode-tools package do you have ?

---

### Post by drorata on 2009-08-22
I am running Ubuntu 8.04, on a Thinkpad X61s. The installed laptop-mode-tools is 1.35-1.

---

### Post by ibuclaw on 2009-08-22
> **drorata said:**
> I am running Ubuntu 8.04, on a Thinkpad X61s. The installed laptop-mode-tools is 1.35-1.

The "other" files you mentioned are available from **intrepid** and upwards packages from Ubuntu.

Also - in future - if you have a question, please start you're own new thread and only reference the threads that you've read. :)

Regards
Iain

---

### Post by Axx83 on 2009-08-22
sorry, your laptop-mode is a couple years older than mine and I discovered those option have been introduced only recently. I don't know if you could just substitute the package with the new one and hope it works with 8.04, probably not. By the way 8.04 is the best ubuntu you can have this days, jaunty is totally unstable and low performing with intel graphics. Try what I said, there's an official laptop-mode website, send an email with those issues.

---

### Post by zoomy942 on 2009-08-25
great thread.

---

### Post by trigoman05 on 2009-10-28
This did not work so well for me. After doing all the recommended changes and making sure laptop mode was enabled, I still get the recommendations from powertop. My battery life was not extended :(

---

### Post by Axx83 on 2009-10-29
You have to check if laptop mode is enabled

run sudo /etc/init.d/laptop-mode status

with ac on and off

if the entri about laptop mode is more than 0 then it's on

otherwise you have to tinker with those file I mentioned in the first page of this topic.

---

### Post by AMTQ on 2010-04-05
thx to Axx83 for the help and explanation! Now I just need powertop to check occasionally how much time is left ;)

---

