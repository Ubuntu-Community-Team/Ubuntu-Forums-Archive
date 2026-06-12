---
title: "FF 3 and Wireless in Ibex(8.10)?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by bytescribe on 2009-04-13
2 Things I need to Address:

1--About FF 3 on Ibex: I requested a copy of Ibex in the mail a few weeks ago, because I was hoping to get a better version of FF 3 (instead of the currently buggy one in Hardy). You might have heard that, in Hardy's FF 3, the history won't record at ALL, and regular bookmarking of sites within FireFox is a no-go. Also, I am not able to use the forward/back/stop/reload buttons. (Not sure why they released FF 3's recent updates before they fixed the bugs)

I've therefore been using Opera so far with Hardy (and may try Epiphany), just so I can use bookmarks and have a recorded history--though it tends to run a bit slower than FF...I've read quite a number of complaints about FF 3 on Ibex (including something about Java), but my boyfriend runs Ibex (64-bit) on his machine and neither he nor I have complaints about FF 3 on this upgrade, Java or no Java. So that's what makes me want to switch from Hardy to Intrepid. Thing is, is my boyfriend's version of FF 3 doing fine *because* he's running 64-bit and not 32? 

In other words, are 32-bit Ibex users having troubles with FF 3 because Ibex MIGHT be programmed to work better in the 64-bit installation? 

Or does it have anything to do with the newness of one's computer (Quentin's only had his new machine a few months)? I ask because I don't want to install Ibex on my 6-year-old Gateway PC thinking I'll see improvements when I might not, therefore making using wireless (my second issue) a moot point.

Please tell me the complaints are in the minority about FF 3 in Ibex, because while I like Opera, and Epiphany may be good, but I REALLLLLY miss using FireFox...and I hate to not support what I think is one of the best (supposedly) browsers out there, despite Firefox's developers jumping the gun on the release of FF 3's recent updates before working out the bugs. 

2--About Wireless on Ibex)

I already have the wireless driver (via ndiswrapper) and certain other necessary drivers blacklisted for Hardy. It's how I am able to type this message at this very moment. And ironically, I am using the otherwise buggy FireFox to type this because FF 3 is STILL faster than Opera. :-P

My dad's CD-ROM drive is still kaput (his priorities are, unfortunately, not high-tech)...but that doesn't bother me because any drivers I need for Ibex that will work with my current Windows-based USB adapter I can download and put on a USB flash drive. I know that I can surreptitiously reset some things in my dad's computer to make the CD-ROM drive work again (in case I need to use the Linksys router software)..I just haven't done it yet. It's a combination of my life taking a drastic turn (I just got one of those rare things called a *job*), and my not wanting to risk my dad getting pissed because I tinkered with (supposedly) his computer--even though he's not willing to set aside and budget the money it will take to get the drive completely wiped, everything fixed and whatnot (the whatnot being that he'd have to get his own disks of WIN XP).

Sooo, without further blah-blah, my questions about wireless with Ibex are. based on my chipset (Ralink) and my USB model # (WUSB54GC) :

1) Do I need a new version of ndiswrapper and, if so, where do I get it?
2) What other drivers would I need for use with Ibex, and if so, where can I get them?
3) Are there any specific Sudo commands I need to know (that might be different from the ones in Hardy) in order to check signal, IP and inet mask addresses, etc?

I might be a little harder to reach this time because I have a swing-shift position (4pm-12 am), but I hope someone can answer my questions.

Blessings,
Kat ^.^

---

### Post by billgoldberg on 2009-04-13
[B]In other words, are 32-bit Ibex users having troubles with FF 3 because Ibex MIGHT be programmed to work better in the 64-bit installation? 
[/B]

After installing Ubuntu 8.10, run the update manager and firefox 3 will be upgraded to the latest version.

I have never had any problems with FF3 on Ibex.

You should be good.

[b]
Or does it have anything to do with the newness of one's computer (Quentin's only had his new machine a few months)? I ask because I don't want to install Ibex on my 6-year-old Gateway PC thinking I'll see improvements when I might not, therefore making using wireless (my second issue) a moot point.
[/B]

The system requirements for Ibex are the same as they were for Hardy.

It should perform about the same (the next Ubuntu version coming out this month should perform better).

[B]
Sooo, without further blah-blah, my questions about wireless with Ibex are. based on my chipset (Ralink) and my USB model # (WUSB54GC) :

1) Do I need a new version of ndiswrapper and, if so, where do I get it?
2) What other drivers would I need for use with Ibex, and if so, where can I get them?
3) Are there any specific Sudo commands I need to know (that might be different from the ones in Hardy) in order to check signal, IP and inet mask addresses, etc?

I might be a little harder to reach this time because I have a swing-shift position (4pm-12 am), but I hope someone can answer my questions.[/B]

I would check first if the wireless card isn't supported OOTB in Ibex.

If it isn't, use ndiswrapper.

1) use the Ubuntu package manager to install ndiswrapper (use an ethernet cable to get internet access).

2) same as with Hardy

3) no, the commands are the same as in Hardy

---

### Post by bytescribe on 2009-04-14
> **billgoldberg said:**
> [B]In other words, are 32-bit Ibex users having troubles with FF 3 because Ibex MIGHT be programmed to work better in the 64-bit installation? 
[/B]

After installing Ubuntu 8.10, run the update manager and firefox 3 will be upgraded to the latest version.

I have never had any problems with FF3 on Ibex.

You should be good.

[b]
Or does it have anything to do with the newness of one's computer (Quentin's only had his new machine a few months)? I ask because I don't want to install Ibex on my 6-year-old Gateway PC thinking I'll see improvements when I might not, therefore making using wireless (my second issue) a moot point.
[/B]

The system requirements for Ibex are the same as they were for Hardy.

It should perform about the same (the next Ubuntu version coming out this month should perform better).

[B]
Sooo, without further blah-blah, my questions about wireless with Ibex are. based on my chipset (Ralink) and my USB model # (WUSB54GC) :

1) Do I need a new version of ndiswrapper and, if so, where do I get it?
2) What other drivers would I need for use with Ibex, and if so, where can I get them?
3) Are there any specific Sudo commands I need to know (that might be different from the ones in Hardy) in order to check signal, IP and inet mask addresses, etc?

I might be a little harder to reach this time because I have a swing-shift position (4pm-12 am), but I hope someone can answer my questions.[/B]

I would check first if the wireless card isn't supported OOTB in Ibex.

If it isn't, use ndiswrapper.

1) use the Ubuntu package manager to install ndiswrapper (use an ethernet cable to get internet access).

2) same as with Hardy

3) no, the commands are the same as in Hardy

So...if I upgrade to Ibex, will the newer version of FF 3 NOT be buggy? In other words, will I have the full bookmarking and history capabilities that I do not seem to have at this very moment? 

Well, what I am using for wireless is not a card but a USB adapter, and I've been using ndiswrapper all this time, so I am going to assume for the time being that I will still have to use ndiswrapper, which is no problem, really. I already HAVE ndiswrapper and the proper driver files for my USB adapter that I can back up onto my USB flash drive while I upgrade. What I am also going to have to do, now that I think about it, is I am also going to have to make a backup file for the current Linux-based wireless driver blacklistings I've got in the "modprobe" folder. 

Here's the thing though, you didn't necessarily answer my question: Does my version of ndiswrapper need to be changed...yes or no?

If yes, then I will have to go downstairs on my parents computer and search for ndiswrapper on some linux repository (even though my parents have Windows), because my dad won't pay an extra $125 to put in ethernet cable running from his computer on the north end of the house alllll the way to my computer on the southeast end...plus it would mean drilling an extra hole in the floor, and Mom's scared stiff of violating our lease, which is another piece of ridiculousness because our landlords are more than amiable people. 

(Not that a little extra research ever hurt me...it's that their computer is a pain in the neck to work with just because it's a Windows machine...but neither of them is a computer geek, so trying to explain to them how ridiculous their so-called "logic" is, is a moot deal.) 

However, if you say I do NOT have to download a new version of ndiswrapper, and that the one I am using with Hardy can be used with Ibex, I can keep the one I already have, plus the accompanying drivers and I can proceed from there.

Looking forward to your further reply.

BB,
Kat ^.^

---

### Post by Jakey_TheSnake on 2009-04-14
I had no problems with FF on hardy, and had none with Ibex, am also having none with jaunty. 

@OP, try uninstalling FF, deleting your ~/.mozilla folder (you'll need to Ctrl + H so you can view hidden), then reinstall using the latest version from the Mozilla site. 

That should fix things _without_ need for an upgrade. 

Regards, 

Jake

edit: NB, it's nice to have someone that has good syntax and can paragraph, too. A lot of people on here can't, and they do my head in to the point where I don't reply. 

You should be able to use the same version of ndiswrapper that you are using currently.

```
rm -rf ~/.mozilla
```
Will delete the mozilla folder, if you're a terminal kinda gal ;) don't be afraid of the "rm -rf", it's not executed as root so couldn't do anything anyway >_>

---

### Post by Bölvaður on 2009-04-14
> **Jakey_TheSnake said:**
> 
```
rm -rf ~/.mozilla
```Will delete the mozilla folder, if you're a terminal kinda gal ;) don't be afraid of the "rm -rf", it's not executed as root so couldn't do anything anyway >_>

except deleting everything that is stated at the end of the line... that is /home/Jakey_TheSnake/.mozilla/ or if there is no path at the end it takes the current path... which isn't nice if you are placed in top level of your home folder -.-


More about wireless.
You might possibly need special kernel version. After updates you should have few new kernels (or just one) which might work either better or worse for your wireless card, depending on if it worked out of the box or not. If it worked on the older kernel you can select it from GRUB (boot loader) and pick the older kernel (you can tell by the numbers). Then try ndiswrapper on both/all kernels if it didnt work without it.

---

