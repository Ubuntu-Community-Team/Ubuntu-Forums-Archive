---
title: "Establishing a connection"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Sedative on 2009-06-05
Hello. I installed Ubuntu as a dual-boot last night with Windows Vista. I am on Vista right now as I cannot get my internet to work on Ubunbtu. I created the connection, entered the key, everything. But the internet won't work and nothing is saying that it's wrong. When I click on the connection bars it asks me for the key again next to my network name, so I put it in, sat there for a few minutes, then it asked me again and again. Can someone help? Give me the correct settings? Anything?

---

### Post by Hospadar on 2009-06-05
Firstly:
Do you know what wireless card you have?
What kind of password is on your wireless (wep-passphrase, wep 128, wpa, etc, etc)?
Have you tried removing the password from your router temprarily and seeing if you can connect properly then?
You might try using different types of password (wep/wpa/etc), sometimes linux drivers don't support all the same types as windows.
Also maybe try going to the driver manager and see if there are some 3rd party drivers for your card (System->Administration->Hardware Drivers)

If you could go into linux and post the output of a couple commands (Applications->Accesories->Terminal) (in "code" blocks if you know how):
```

ifconfig #info about your connection
iwconfig #wireless info
sudo lshw -C network #more detailed network info
lspci #some other hardware info

```You can just copy paste that whole block, make sure all the commands run.
You can copy paste the results into a text document in ubuntu and then paste it up here (open linux text files in windows with wordpad, not notepad)

This info would help diagnose the problem.

---

### Post by carml on 2009-06-05
What kind of connection are you trying to use: Ethernet,wireless,internet key?
Is could help to know a little more ;)

---

### Post by Sedative on 2009-06-05
I'm trying to have a wireless connection. And @Hospadar: I have no idea what you're saying. :(

I don't know what a wireless card is. I'm using WEP something. And I'm afreaid to delete what's in my terminal to replace it with that. Do I replace it or write under what is already written there?

---

### Post by carml on 2009-06-05
He is asking you to turn off Vista,boot with Ubuntu and go to Applications->Accessories->Terminal and type the commannds you see,the ones like "ifconfig" etc.
I hope I cleared your doubts:)

---

### Post by Sedative on 2009-06-05
Alright. I'm on my parents computer right now and going back and forth typing that. It's all one big line though since I can't do enters.

EDIT: Okay this isn't working out for me. Is there anything else I can do?? Does EVERYONE have to do this to get connected?

---

### Post by Hospadar on 2009-06-05
Each line is just one command, you can run them one at a time

---

### Post by Sedative on 2009-06-05
And then what happens?

---

### Post by Celauran on 2009-06-05
Enter the commands listed above and post the output here. So enter

```
ifconfig
```
it's going to print some output to screen, which you will then paste here. Repeat for each command above. This will give us some more detailed info about your system, so we'll be better equipped to help you.

---

### Post by Sedative on 2009-06-05
Okay. And how do I post it here? I'm posting on here from my parents computer and Ubuntu is on my computer: where I'm doing the work.

---

### Post by Celauran on 2009-06-05
Redirect output to a file then copy the file over via USB stick?

```
ifconfig > ifconfig.txt
sudo lshw -C network > lshw.txt
```
and so on.

---

### Post by Sedative on 2009-06-05
Oh, I don't have any of those laying around, sorry. I guess I'll wait for my dad to get home late, late tonight. =/ I'm sorry I couldn't provide you all with the information needed. 
If anyone knows what the problem is without the terminal info, feel free to still post please!

---

### Post by nothingspecial on 2009-06-05
Wireless works for most people straight away.

There are some cards that can seem a bit tricky to get going at first.

Nobody can help you if they don`t know the card you have.

If you type ```
sudo lshw -C network
``` on your ubuntu computer it will give some imformation like this```
[CODE]

[CODE]description: Wireless interface
       [COLOR="Red"]product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation[/COLOR]
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:4b:bb:f0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.5 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
```[/CODE]

Hopefully just the bit in red will be what someone needs to help. Whatever it says on your system, write it down and post it exactly.

---

### Post by Sedative on 2009-06-05
Okay, when I typed this:

```
sudo lshw -C network
```


I got this (where you highlighted):

```
product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
vendor: Intel Corporation
```

---

### Post by nothingspecial on 2009-06-05
Try typing this
```

sudo modprobe -r iwlagn
```

```
sudo modprobe iwlagn
```

and try to connect again.

For now you may have to do this every time you boot. It removes and puts back your wireless driver. I found the bug report [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378189")

I hope that sorts it.

---

### Post by Sedative on 2009-06-05
Nothing happened. I can't even ask for it to connect, because 

"Wired Network
disconnect
Wireless Network"


Are all paled so I can't click on them.

---

### Post by Sedative on 2009-06-05
Sorry, but I **really** need help. Bump.

---

### Post by Sedative on 2009-06-05
Guys! I need help BADLY!!

---

### Post by RevCriz on 2009-06-05
A bump for you

---

### Post by Curvature_Tensor on 2009-06-05
Does your internet work using a wired connection?

here are all the things I have found to try:

1.  sudo gedit /etc/modprobe.d/bad_list
 
Add this line
alias net-pf-10 off
 
Save and Restart
[http://www.linuxforums.org/forum/deb...some-help.html]("http://www.linuxforums.org/forum/debian-linux-help/19137-ubuntu-cannot-connect-internet-need-some-help.html")

2. 
sudo gedit /etc/modules
add dmfe

sudo gedit /etc/modprobe.d/blacklist
blacklist tulip

[http://ubuntuforums.org/showthread.php?t=186430](http://ubuntuforums.org/showthread.php?t=186430)

3. Realtek fix not relevant but listing it here for reference purposes
[http://ubuntuforums.org/showthread.php?t=5384484](http://ubuntuforums.org/showthread.php?t=5384484). booting in recovery mode

4. "...I chose the first option 'Ubuntu, kernal 2.6.15-23-386' and hit 'e' to edit. Then I went to the second line 'kernel /boot/vmlinuz-2.6.15-23-386...' and hit 'e' to edit. At the very end of the line I added 'irqpoll' (without the quotes) ..."
[http://ubuntuforums.org/showthread.php?t=187316&page=2](http://ubuntuforums.org/showthread.php?t=187316&page=2)

---

