---
title: "wireless switch does not work"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by bekirs on 2016-01-30
Hello,

Today I received a system error after I started my laptop. Since then, the wireless does not work and it is not possible to activate it by pressing to the wireless switch on button.

Could you please help me with this issue?

Regards,

---

### Post by sandyd on 2016-01-30
Your thread has been moved to *Networking & Wireless*

---

### Post by bekirs on 2016-01-31
Hello,

I lost all types of internet connections after an error message I received yesterday morning. Internet works fine with another computer, so the problem seems to originate from my laptop with Xubuntu system.

Could you please help?

---

### Post by matt_symes on 2016-01-31
Hi

Are you being affected by this regression ? Many are unfortunately.

[https://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet](https://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet)

Kind regards

---

### Post by bekirs on 2016-01-31
Applying Step 2 solved the problem with the wired internet.. thanks.
However, I still have no wireless connection. Do you know a solution for that?

---

### Post by matt_symes on 2016-01-31
Hi

> **bekirs said:**
> Applying Step 2 solved the problem with the wired internet.. thanks.
However, I still have no wireless connection. Do you know a solution for that?

The fix above should have fixed both wired and wireless problems.

What exactly is the problem with wireless ?

Can you enable wireless in nm-applet ?

Is the wireless driver loaded ?

What does this return ?

```
nmcli g
```

Can you post the output of

```
ifconfig -a
```

Kind regards

---

### Post by bekirs on 2016-01-31
When I try to activate the wireless by pressing to the related key, the red color (passive) does not turn to blue (active). I, however, observed that this action changes some parameters in the output of **rfkill list all** 

I don't know how to activate wireless via **nm-applet**. I don't know either what **nm-applet** is.

Wireless was working since several years without problem. I assume that the drive is loaded.

Here are the outputs you asked for:
```
:~$ nmcli g
Error: Object 'g' is unknown, try 'nmcli help'.
```

```
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e4:11:5b:ef:13:fd  
          inet addr:192.168.0.135  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e611:5bff:feef:13fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121658745 (121.6 MB)  TX bytes:17743169 (17.7 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228897 (228.8 KB)  TX bytes:228897 (228.8 KB)


wlan0     Link encap:Ethernet  HWaddr 74:de:2b:9e:20:9b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

---

### Post by matt_symes on 2016-01-31
Hi

> **bekirs said:**
> When I try to activate the wireless by pressing to the related key, the red color (passive) does not turn to blue (active). I, however, observed that this action changes some parameters in the output of **rfkill list all** 

Can you post what those changes are please.

> I don't know how to activate wireless via **nm-applet**. I don't know either what **nm-applet** is.

nm-applet is the network icon on the top panel that you can use to join wireless. You can left click on it and there should be an option to enable and disable both 'networking' and 'Wi-Fi' or 'Wireless'.

> Here are the outputs you asked for:
```
:~$ nmcli g
Error: Object 'g' is unknown, try 'nmcli help'.
```

You must have be using an older version of nmcli than i am as the 'g' object means 'general' on this xenial installation.

Can you post the output of 

```
cat /etc/lsb-release
```

> 
Wireless was working since several years without problem. I assume that the drive is loaded.

> ```
:~$ ifconfig -a

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:9e:20:9b  
          **BROADCAST MULTICAST**  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

This looks to be the problem. Your wifi driver should be loaded and the wireless interface has been created, however your wireless interface is not *'UP'*. Not quite sure why that should be.

It may be due to Wi-Fi being disabled in nm-applet as i mentioned above.

Left click on the network icon on the top panel, on the right hand side. 

Look for the entry that states

```
Enable 'Wi-Fi'
or
Enable Wireless
```

and make sure it's got a tick next to it. 

If it has no tick next to it then left click it.

Does this fix Wi-Fi ?

Kind regards

---

### Post by bekirs on 2016-01-31
Current output after **rfkill list all** (before pressing to the wireless key):

```
:~$ rfkill list all0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

Output of **rfkill list all** after I press to the wireless key:
```
:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
3: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes

```

I think I understand what you mean with **nm-applet** but I guess I lost this icon after upgrading my distribution and never got it back. Currently, I don't have it...

Output of **cat /etc/lsb-release**:
```
:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
```

---

### Post by praseodym on 2016-01-31
Is it a BIOS or an (U)EFI? If BIOS reset it to default settings

---

### Post by bekirs on 2016-01-31
How can I find out that?

---

### Post by praseodym on 2016-01-31
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```
Here it shows "BIOS"

---

### Post by bekirs on 2016-01-31
It is BIOS...

I restarted my laptop and pressed F10 in order to reach BIOS. 
Default Settings are loaded and I exit the BIOS with Save&Close.

I am still missing the **nm-applet**.

wireless is back again... I don't know why and how, but it works.

**nm-applet** is still missing.

---

### Post by matt_symes on 2016-02-01
Hi

> **bekirs said:**
> wireless is back again... I don't know why and how, but it works.

**nm-applet** is still missing.

Please post the output of these commands.

```
which nm-applet
```

```
dpkg -l network-manager-gnome
```

```
apt-cache policy network-manager-gnome
```

If the above commands show that network-manager-gnome is installed and that nm-applet exists on your system then you need to look to see if nm-applets being autostarted when you log into Xubuntu.

Menu->All Settings->Session and Startup->Application Autostart (It's the third tab.)

Look for the entry that says "Network (Manage you network connections)" and ensure there is a tick next to it.

Log out and then log back in.

Do you have nm-applet in the top panel ?

Kind regards

---

### Post by bekirs on 2016-02-01
Here are the outputs of the commands:
```
:~$ which nm-applet/usr/bin/nm-applet

```

```
:~$ dpkg -l network-manager-gnome
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  network-manage 0.9.8.8-0ubu amd64        network management framework (GNO



```

```
:~$ apt-cache policy network-manager-gnome
network-manager-gnome:
  Installed: 0.9.8.8-0ubuntu4.4
  Candidate: 0.9.8.8-0ubuntu4.4
  Version table:
 *** 0.9.8.8-0ubuntu4.4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.8.8-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages



```

I checked the status of **[COLOR=#000000]Network (Manage you network connections)[/COLOR]**[COLOR=#000000], there was already a tick next to it.

[/COLOR]I don't see **nm-applet** on the top panel after logging out & in again.

---

### Post by matt_symes on 2016-02-01
Hi

It looks to be installed correctly.

Let's try some diagnostics quickly.

Open a terminal and type

```
nm-applet
```

Do you get the applet appearing in the top panel ?

If not then post the terminal output here.

If so then post back to say that you do.

At least we know what the problem isn't :)

**EDIT:**

Do you have any indicators displayed on the panel ? Do you have the sound control or the mail indicator and others ?

Kind regards

---

### Post by bekirs on 2016-02-01
no response after nm-applet

```
:~$ nm-applet




```

The cursor is blinking... there's no new command line such as xxx@xxx: ~$

There are some indicators, e.g. Dropbox, keyboard language... but sound control is missing as well..

I tried the same command after [B]sudo su

[/B]```
nm-appletnm-applet-Message: using fallback from indicator to GtkStatusIcon



```

The cursor is still blinking and when I close the terminal, the message is "There is still a process running in this terminal. Closing the terminal will kill it."

By the way, it appeared an icon (up & down arrows), which is, I assume, related to **nm-applet**??

---

### Post by matt_symes on 2016-02-01
Hi

> **bekirs said:**
> By the way, it appeared an icon (up & down arrows), which is, I assume, related to **nm-applet**??

That sounds like nm-applet. Did it also appear when you ran the command without *sudo* ?

If the sound indicator is missing as well then your problems run deeper than just nm-applet.

Can you take a screenshot, with and without running nm-applet, so i can see exactly what you have.

Attach them to your next post.

Can you also post the output of (just to double check something odd is not going on there)

```
dpkg -l xfce4-indicator-plugin
``` 

Kind regards

---

### Post by bekirs on 2016-02-01
Output is as follows:

```
:~$ dpkg -l xfce4-indicator-pluginDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xfce4-indicato 2.3.2-0ubunt amd64        plugin to display information fro



```

---

### Post by matt_symes on 2016-02-01
Hi

So you only see nm-applet when running sudo. I'm wondering if this is some permissions issue or somthing.

Can you post the output of

```
ls -l ~/.config/dconf
```

and

```
ls -ld ~/.config/dconf
```

Then install dconf-cli using this command

```
sudo apt-get install dconf-cli
```

Can you post the output of this command below.

```
dconf read /org/gnome/nm-applet/show-applet
```

and finally this one.

```
cat /etc/xdg/autostart/nm-applet.desktop
```

EDIT:

Better check this as well.

```
ls -l $(which nm-applet)
```

Kind regards

---

### Post by bekirs on 2016-02-01
```

:~$ ls -l ~/.config/dconftotal 28
-rw-rw-r-- 1 bekirsalgin bekirsalgin 24843 Feb  1 21:44 user

```

```

:~$ ls -ld ~/.config/dconf
drwx------ 2 bekirsalgin bekirsalgin 4096 Feb  1 21:44 /home/bekirsalgin/.config/dconf

```

```

:~$ sudo apt-get install dconf-cli
[sudo] password for bekirsalgin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dconf-cli is already the newest version.
dconf-cli set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is to be installed
 libnl-route-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

:~$ dconf read /org/gnome/nm-applet/show-applet

```

```

:~$ cat /etc/xdg/autostart/nm-applet.desktop
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=false
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-UsesNotifications=true
AutostartCondition=GNOME3 unless-session gnome
X-Ubuntu-Gettext-Domain=nm-applet

```

---

### Post by matt_symes on 2016-02-01
Hi

> ```

:~$ ls -ld ~/.config/dconf
drwx------ 2 bekirsalgin bekirsalgin 4096 Feb  1 21:44 /home/bekirsalgin/.config/dconf

```

On my system the permissions are slightly different. If you run they will be the same as mine. They can be reverted later if necessary.

```
chmod 775 ~/.config/dconf
```

> ```

:~$ sudo apt-get install dconf-cli
[sudo] password for bekirsalgin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dconf-cli is already the newest version.
dconf-cli set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is to be installed
 libnl-route-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

You package system is currently broken. Attempting to fix it may put you back in the position of having no wireless though so we can look at that later.

> ```

:~$ dconf read /org/gnome/nm-applet/show-applet

```

This is odd and unexpected. Do you not have a key for nm-applet ?

Can you post the output of this command

```
dconf list /org/gnome/
```

and 

```
dconf list /com/canonical/indicator/
```

and finally, let's search the databases for them

```
dconf dump / | egrep "nm-applet|sound"
``` 

I'm wondering if you need to reset some keys in your dconf database as well.

Have you played with dconf before ?

Kind regards

---

### Post by bekirs on 2016-02-01
I didn't play with **dconf** before..

```

:~$ dconf list /org/gnome/
settings-daemon/
gedit/
calculator/
gnome-system-log/
nautilus/
evince/
file-roller/
deja-dup/
desktop/
mahjongg/
gthumb/
eog/
gnome-sudoku/
liferea/
Totem/
gnumeric/
nm-applet/

```

```

:~$ dconf list /com/canonical/indicator/
keyboard/

```

```

:~$ dconf dump / | egrep "nm-applet|sound"
[org/gnome/nm-applet]

```

---

### Post by matt_symes on 2016-02-01
Hi

> **bekirs said:**
> ```

:~$ dconf dump / | egrep "nm-applet|sound"
[org/gnome/nm-applet]

```

You have the nm-applet key and that is good.

The fact that *dconf read /org/gnome/nm-applet/show-applet* did not return anything may not be the problem i thought it was.

It looks like dconf only display keys that have been explicitly set. It does not display the default keys and i was not expecting that.

We could try setting it explicitly and see what happens. We have nothing to lose.

From the terminal

```
dconf write /org/gnome/nm-applet/show-applet true
```

Check it's been set with..

```
dconf read /org/gnome/nm-applet/show-applet
```

It should display *true*.

Reboot your PC and see if you get the applet.

I'm not sure this will fix it but it's worth a try. Post back if you have success.

I must admit to being a bit mystified as why it's not displaying nm-applet and why you can only get it to display using *sudo*.

This smacks of a permissions problem somewhere on your system. The problem is knowing where :)

I may have to think about this overnight if setting it explicitly does not fix it.

Kind regards

---

### Post by bekirs on 2016-02-01
After the commands, it indeed displayed true. However, there is still no nm-applet after reboot. Typing nm-applet in the command line did not change the result.

---

### Post by matt_symes on 2016-02-01
Hi

> **bekirs said:**
> After the commands, it indeed displayed true. However, there is still no nm-applet after reboot. Typing nm-applet in the command line did not change the result.

I'm going to have to think about this for a while as everything you've posted so far looks good.

I'll post back tomorrow evening. It'll also give another day for other people to look at this thread.

Kind regards

---

