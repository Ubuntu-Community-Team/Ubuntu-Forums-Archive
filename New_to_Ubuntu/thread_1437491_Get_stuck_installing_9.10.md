---
title: "Get stuck installing 9.10"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Pgdsm on 2010-03-24
I've got an older laptop with a Japanese xp installed on it.
P4 1.9 256 mb ram and 60gb hard drive
I have a burnt copy of 9.10 and a copy from canocial. Both disks give me the same problem.
When trying to install I first just got a black screen with a flashing underscore in the top left.
I tried VGA=771 with no luck. Acpi off noapic off and nolapic off it will get to the screen where I choose my language, after I press forward it hangs up for a while then goes to an orange background then switches to the ubuntu logo and repeats. I did a memtest and no errors were found. I was able to use live once but can't even get back to that now. I am really starting to pull my hair out here. Would really like to bring this older laptop back too life as xp is horrible slow on it. ( 11-12 min startup) plus the fact that I can't read Japanese and my gf can't translate it too well. Lol

thanks in advance

---

### Post by phidia on 2010-03-24
I don't have the minimum requirements in front of me but 256MB of ram might be insufficient for a graphical install. You could dl the alternate iso or look at lighter weight distros (zenwalk, damsmall, puppy & others). See distrowatch.com

PS: You might also want to provide the complete specs (manufacturer, model) & especially what graphics card the laptop has.

---

### Post by |{urse on 2010-03-24
This problem sounds degenerative so I'm gonna say either video memory or hard drive, most likely hard drive. Go get a copy of hiren's boot cd and run hdd regen to see if theres (hopefully repairable) bad blocks. While youre in hiren's (a livecd just like ubuntu) you can run pcdoctor motherboard diagnostics to narrow down things further if the hard disk checks out okay.

Edit: or it's just good old-fashioned overheating, are all fans spinning? (at some point they should in the span of 5 mins after post)

---

### Post by Pgdsm on 2010-03-24
I understand that 256 is the minimum. I just wanted to stick with ubuntu as I just put that on my desktop. Still getting used to Linux ( one week in) what would you recomend that is similar to ubuntu?
I will check into other distro and go back to xp for now

when I do the memtest and it came back with no errors that would make me think the HD is good no?

---

### Post by phidia on 2010-03-24
memtest is checking the ram not the hard drive I believe. Try xbuntu or lbuntu for lighter weight and the alternate (which is not a livecd) is sometimes easier to install from. It's also not a graphical install which makes it easier on a low ram machine. If xp is still booting there's no reason to go on a hunt for hardware problems btw.

Here is the [link]("http://www.ubuntulinux.org/getubuntu/downloadmirrors#alternate") including tutorial for the alternative.

---

### Post by Pgdsm on 2010-03-24
The laptop doesn't seem to be over heating fans are coming on and off. 
Forgot to mention this is a toshiba dynabook e8/x19pde
only problem with getting a diff distro is this is the only comp with a burner and it took me a looonng time to get everything in order to burn the first copy. ( also got one mail ordered)
I did a defrag on xp and the HD seemed ok.

Edit graphics safe mode just gives me a white screen

---

### Post by phidia on 2010-03-24
> **Pgdsm said:**
> The laptop doesn't seem to be over heating fans are coming on and off. 
Forgot to mention this is a toshiba dynabook e8/x19pde
only problem with getting a diff distro is this is the only comp with a burner and it took me a looonng time to get everything in order to burn the first copy. ( also got one mail ordered)
I did a defrag on xp and the HD seemed ok.

I can understand why |{urse brought up the HD an 11 minute boot up using xp does seem excessive but I don't know all of what's loading there. If xp runs I'm going to think the hardware is ok but who knows. Using the alternative install cd could be the answer but you need to get it somehow.

Maybe a friend can dl  and burn it for you?

---

### Post by ankspo71 on 2010-03-24
Hi, 
According to a page last edited  2010-03-13, the recommended minimum requirements is 384mb. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
It also says it can be installed on systems with as low as 64mb, but it would require the use of an alternate install cd. I think Ubuntu 9.04 was the last of the 256mb minimum memory requirements (using a live cd).
Hope this helps.

---

### Post by |{urse on 2010-03-24
> **phidia said:**
> If xp is still booting there's no reason to go on a hunt for hardware problems btw.

You're wrong, but okay. Just because one OS boots doesnt mean there aren't hardware problems, you generally don't see the real brunt of these issues until you try to install an OS. btw. That's why memtest is on the gosh darn disk. ^_- Do you actually know which OS is more fault tolerant with what hardware issues or are you just assuming?

---

### Post by mastablasta on 2010-03-24
> **ankspo71 said:**
> Hi, 
According to a page last edited 2010-03-13, the recommended minimum requirements is 384mb. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
It also says it can be installed on systems with as low as 64mb, but it would require the use of an alternate install cd. I think Ubuntu 9.04 was the last of the 256mb minimum memory requirements (using a live cd).
Hope this helps.
 
 
I do not knwo about installing however i can confirm that Ubuntu 9.10 LiveCD works well with 256 MB ram (16MB of this goes for graphics card) and faster or same speed is achieeved from CD than with XP. Also Mint 8 and Xubuntu (live CD) work well. Mint is a bit slow. Xubuntu also on this computer. Ubuntu was/seemed much faster.
 
However for graphical install you might really need either more ram or you can simply use altenate non graphical one. I haven't installed Ubuntu on that laptop as i can not find a way to propperly back up the XP currently installed there.

---

### Post by Pgdsm on 2010-03-24
Xp takes so long cause there are a tonne of programs at startup! I justcant find the startup folder ( it's all Japanese)
will try alternate and see what happens

---

### Post by phidia on 2010-03-24
> **|{urse said:**
> You're wrong, but okay. Just because one OS boots doesnt mean there aren't hardware problems, you generally don't see the real brunt of these issues until you try to install an OS. btw. That's why memtest is on the gosh darn disk. ^_- Do you actually know which OS is more fault tolerant with what hardware issues or are you just assuming?

No your wrong. So what does that prove? 

If an OS boots it proves to me that the hardware is functioning enough to get it to boot. I've been involved in hardware and IT QC so I do understand. I understand that people often jump to some conclusion based on almost nothing and want to start replacing things. 

Now if the alternate iso doesn't work properly assuming it was downloaded and burned correctly then I might consider looking at hardware but the trouble shooting rule in most workplaces is do what's easiest and simplest first not the other way around.

---

### Post by Pgdsm on 2010-03-24
Hardware could be a problem but I doubt it. The battery is absolutly useless though. ( won't hold a charge for even a second) 
really though my aim with this is to have a nice lil laptop ( 15 inch screen) lightweight ( no battery jst plugged in)
and be able to watch movies on check email and play music all while not leaving the bed. Also when I go out of town to use for video chat with my fiancé. It is her old computer that she upgraded from cause it was too slow.

---

### Post by Pgdsm on 2010-03-26
Ok so I finally got the alternate iso dowloaded and burnt.
Went to instal it and it wouldn't let me partition the drive, went back into windows and shut down properly.
Partition worked after that. Spent nearly an Hour to install and partition the drive. 
When I went to boot up ubuntu after everything was done, it keeps looping through the purple ubuntu screen ( the one with the startup noise)
what would be causing this and what can I do? This is a lot of hassle but I want to get it sorted out sooner than later
thank in advance

---

### Post by |{urse on 2010-04-02
> **phidia said:**
> No your wrong. So what does that prove? 

If an OS boots it proves to me that the hardware is functioning enough to get it to boot. I've been involved in hardware and IT QC so I do understand. I understand that people often jump to some conclusion based on almost nothing and want to start replacing things. 

Now if the alternate iso doesn't work properly assuming it was downloaded and burned correctly then I might consider looking at hardware but the trouble shooting rule in most workplaces is do what's easiest and simplest first not the other way around.

Well if we are going to flaunt credentials then I'm a government contractor and a systems engineer for several companies as well. Fact of the matter is that windows is more fault tolerant with bad ram, which means just because it boots doesn't mean your ram is okay. That's not my opinion its just a fact.  That was my point. I never presented that as the appropriate next course of action in this matter. i was only responding to the statement "If xp boots then its not hardware" Now if you can tell me why windows damn near ignores the first parity bit on bad column addresses then I'll apologize.

---

