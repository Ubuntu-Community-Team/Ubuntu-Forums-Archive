---
title: "How To: Wireless on a Fujitsu Siemens Li 2727 notebook"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by randysparks on 2008-11-18
This should work for all the annoying notebooks in the Fujitsu Siemens range that require a special software switch to activate wifi, although it's only tested on an Li2727 notebook. 

**These steps are nice and easy. No compiling modules, as the other (older) guides suggest. ** Please post links to this guide wherever you find these outdated guides.

EDIT:  If using Jaunty (9.04), there's no need for step 1 & 2. Just skip straight to step 3. 

1. Get online via an Ethernet cable and use Synaptic to install either of these packages (hit the Reload button before installing, as you should always do):

```
linux-backports-modules-hardy 
linux-backports-modules-intrepid
```

Get the Hardy one if you're using Ubuntu 8.04, or the Intrepid one if you're using Ubuntu 8.10.

2. Update the system (sudo apt-get update, or use the program on the System -> Administration menu).

3. You can now go online straight away, although only until you reboot, by typing the following into a terminal window:

```
sudo modprobe acerhk
echo on > /proc/driver/acerhk/wirelessled
```

Wait a few seconds for wifi networks to appear in Networkmanager. Note that they won't appear instantly. 

However, to make the change permanent, you'll need to do the following:

Open a terminal window and type the following to edit /etc/modules:

```
sudo nano /etc/modules
```

4. Add a new line at the end that reads simply

```
acerhk
```

Save the file (Ctrl+X, Y, hit Enter).

5. Create a new text file as follows:

```
sudo nano /etc/rc2.d/S19wifiactivate

```
In the new text file, type the following:

```
echo on > /proc/driver/acerhk/wirelessled
```

Save the file (Ctrl+X, Y, Enter).

6. Type the following to make your new file executable

```
sudo chmod +x /etc/rc2.d/S19wifiactivate

```
7. Reboot. When Ubuntu returns to service you should now have wireless working fine. No need to enable it using the keyboard shortcut. 

To control the screen brightness, just add the Brightness applet to any panel. The keyboard shortcut keys don't work.

---

### Post by super.rad on 2008-12-17
Thanks I'd tried so many guides to get the wireless working on my gf's new laptop and none of them had worked. This was by far the easiest and worked perfectly

---

### Post by suspicion4u on 2008-12-17
Not to crash the parade on anybody else's how to but I lost the widgets panel and my desktop in kde's version of intrepid ibex and I cant seem to get it back after trying almost this whole week so if somebody could assist with that it'll be greatly appreciated.  Im sure its something simple but its just not coming to me

---

### Post by zeroms on 2009-01-25
Great job!
Thank you!

P.S.: One more thing needed if it is possible and someone from here know how can I set up to work the Fn+F1 to turn on/off the Wireless? (Sometimes I'm using wired connection)

---

### Post by iklein on 2009-02-17
Great thanks!
You are my savior!!!

---

### Post by randysparks on 2009-02-24
> **zeroms said:**
> Great job!
Thank you!

P.S.: One more thing needed if it is possible and someone from here know how can I set up to work the Fn+F1 to turn on/off the Wireless? (Sometimes I'm using wired connection)

To turn off the wifi, you should be able to type the following:

sudo echo off > /proc/driver/acerhk/wirelessled

It looks like there's still no support for the Li2727's hotkeys in any version of Ubuntu :(

---

### Post by iklein on 2009-02-28
I found "acerhk-source" in Synaptic. This driver will give access to the special keys which are not handled by the keyboard driver. It should work on Fujitsu-Siemens.

Try.

---

### Post by iklein on 2009-03-01
It doesn't work on my 2727.

---

### Post by super.rad on 2009-03-07
This worked for me on intrepid until there was a kernel update, now I'm using Jaunty and have followed the guide again and after rebooting the wireless led is on but ubuntu shows no wireless devices. Before I tried this guide it could see the wireless card but it never worked (and the led was never on) any suggestions?

---

### Post by anastuta on 2009-04-03
@ randysparks,  :guitar: 

Thanks for the guidance, it worked for me, Fujitsu Siemens Amilo PA 3515, for wireless. Now I am writing this message wireless connected. Of course I have Ubuntu 9.04 Jaunty i686.

   thanks again ):P

---

### Post by heyho on 2009-04-13
Many thanks randysparks.

Worked for me ( Amilo Li 1718 ) on intrepid. After a couple of weeks fiddling, this finally sorted the issue.

I already had ath5k via backports, but was struggling to activate the card - I am a happy man!

---

### Post by calrogman on 2009-05-24
This does not work on the Li 2735.

---

### Post by cj13579 on 2009-06-03
Great guide. Thank you very much! :D

---

### Post by fonorobert on 2009-06-29
Hi everyone. I tried several guides, and had several problem. For this one, I had the following:

when I type in the terminal 


sudo modprobe acerhk

It returns : FATAL module acerhk not found.

Help me! what to do? 

Pls. Write to me to [EMAIL="angol.informatika@gmail.com"]angol.informatika@gmail.com[/EMAIL]
thx

---

### Post by Dragonfi on 2009-07-02
I have the exact same problem fonorobert decribed:

```

$ sudo modprobe acerhk
FATAL: Module acerhk not found.

```

Also I run Ubuntu 9.04 64bit

Now searching on how to get the module...

UPDATE:
I found a package named **acerhk-source**. I guess it's the source code for it, but I dont know exacly how to create the kernel module from it.

UPDATE:
I have managed to build it. Now I only have to figure out how to use it correctley...

UPDATE:
I kind of lost the threads somewhere.. I hope someone would be able to sort them out for me.

---

### Post by De Baimbo on 2009-07-27
Thanks a lot, this nearly worked for me on Li 2727.
The problem now is that it always disconnects after a couple of minutes! And I always have to try several times to get it connected again.
Since I am on Ubuntu 9.04 I skipped the first two points of the guide, are you sure I don't need those packages?

---

### Post by Dragonfi on 2009-07-28
the acerhk module is already loaded (I fiddled with it a while back), but when I send on to the wirelessled, nothing happens.

I have the ath5k module inserted too, the wireless device is properly detected. ( I can see it in lshw and iwconfig ).

Any ideas? Also, any request for more information? ( output of modprobe and such )

---

### Post by De Baimbo on 2009-07-28
I installed the package linux-backports-modules-jaunty but the problem remains, it disconnects every 2 minutes. 
By the way, I am always working with my laptop really close to the router, so that the signal is strong.

---

### Post by Dragonfi on 2009-07-28
I've tried using the acer-wmi module, and it works ( for me at least, using Ubuntu 9.04)

---

### Post by Megaptera on 2009-08-11
randysparks,
thanks so much for that guide it worked spot on first time on my son's Amilo Li2727 laptop. He'd been desperate to try out Linux Mint and your guide made it possible!!

Many thanks from the two of us.

---

### Post by MLicense on 2009-08-28
I love you! I spent best part of a day and a half trying to get the wireless working on this!

Thanks so much.

---

### Post by mckooiker on 2009-11-15
I'm working on my amilo Li 2732 now, and since ubuntu 9.04, the only thing you have to do to het the wireless working is:
1) get rid of the ath_pci module (sudo rmmod ath_pci)
2) activate acer-wmi module (sudo modprobe acer-wmi)

---

### Post by hamstermoon on 2009-12-09
When I did that (Mine is a 2727 apparently when I looked under the comp!) says 'module ath_pci does not exist in /proc/modules'
 
I am working on Karmic so I am not sure if that is the problem?

---

### Post by cj13579 on 2009-12-09
> **hamstermoon said:**
> When I did that (Mine is a 2727 apparently when I looked under the comp!) says 'module ath_pci does not exist in /proc/modules'
 
I am working on Karmic so I am not sure if that is the problem?

I am using a 1718 but followed this guide when on Jaunty and it worked perfectly. You may find that this, although for the 1718, works for you:

[http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt](http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt)

---

### Post by Cookiecraig on 2009-12-10
[I][B]I'm working on the Amilo 2735, Does this guide differ in any way?

I haven't tried yet because it seems to complicated.[/B][/I]

---

### Post by Alethi0 on 2010-01-03
Tried on Ubuntu 9.10, didn't seem to work. Restarted, no Wireless LED and wireless not working at all. Any ideas?

---

### Post by cj13579 on 2010-01-03
> **Alethi0 said:**
> Tried on Ubuntu 9.10, didn't seem to work. Restarted, no Wireless LED and wireless not working at all. Any ideas?

Have you tried using this quide for 9.10:

[http://www.edbl.no/karmic/amilo_1718...buntu_9.10.txt](http://www.edbl.no/karmic/amilo_1718...buntu_9.10.txt)

---

### Post by Seraphica on 2010-02-05
I did it on my friends laptop and it worked. ;) He was using Ubuntu 9.04. After the upgrade to 9.10 the wireless wasn't working anymore. :( I believe it didn't have "acerhk" anymore. Does anyone else know something about this? What can i do to get wireless back working? Do i need to find a way to install "acerhk" again and then use the same method to get wireless to work? Please help.

---

### Post by narel (at) utumno on 2010-04-17
I've just installed 10.04 (beta2) on F-S Li 2727 and wifi still doesn't work by default. But this should help:

modprobe -r ath5k
modprobe acer_wmi
modprobe ath5k

---

### Post by erriqk on 2010-05-06
and wat should I do, before I am using these commands?

---

### Post by Matt__ on 2010-05-16
there is a very simple hardware hack to overcome the wireless signal kill on the Amilo 2727 li (Atheros AR5001 to 5005) that involves less than 5 mins with a screwdriver and a piece of masking tape.
Ive tried it and it works a dream

[Instructions can be found here]("http://forum.ts.fujitsu.com/forum/viewtopic.php?t=34742")

---

### Post by queBurro on 2010-05-17
ok, for anyone googling and ending up here, there's a bios update (1.10) for the Amilo li2727 that leaves the wireless in an enabled state which seems to have fixed the hotkey problem :)

---

### Post by black87 on 2010-06-19
> **narel (at) utumno said:**
> I've just installed 10.04 (beta2) on F-S Li 2727 and wifi still doesn't work by default. But this should help:

modprobe -r ath5k
modprobe acer_wmi
modprobe ath5k

Even though I'm a man, I want to have your babies. Thanks! =D>

Finally got wireless working using this on my AmiloPa3515

---

### Post by mx18bp on 2011-05-10
> Re: How To: Wireless on a Fujitsu Siemens Li 2727 notebook
I've just installed 10.04 (beta2) on F-S Li 2727 and wifi still doesn't work by default. But this should help:

modprobe -r ath5k
modprobe acer_wmi
modprobe ath5k

This also helped me on my amilo 2727, so I my screwdriver could be left in its case!

---

### Post by Rankin1 on 2011-05-22
Does this work with the new Ubuntu 11.04

---

