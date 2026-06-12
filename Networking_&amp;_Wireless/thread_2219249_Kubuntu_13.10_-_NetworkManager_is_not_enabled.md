---
title: "Kubuntu 13.10 - NetworkManager is not enabled"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by morgenstern2 on 2014-04-23
Back home after three months i'm trying to connect my kubuntu 13.10 tu home DSL connection, with an ethernet cable; this connection worked fine before i left and is working fine now with other computers. 
This time the connection didn't seem to work, i struggled a bit with the network manager and now it doesn't work at all since some days. 
The applet in the tray says "NetworkManager is not enabled" and the connection doesn't work.
The "network enabled" option is not toggled by default by toggling it doesn't help. In the last days i already tried some workarounds (see in the following link), nothing helped.

[https://diasp.org/posts/2978786](https://diasp.org/posts/2978786)

Any idea?

---

### Post by SeijiSensei on 2014-04-23
First I would recommend upgrading to the 14.04LTS release of Kubuntu since 13.10 will no longer be supported [after July]("https://wiki.ubuntu.com/Releases").  Then see if that works better.  You should be able to run "sudo do-release-upgrade" and let Kubuntu handle the rest.

You'll need to get a network connection first.  You can do this manually using an Ethernet cable like this.  First, pick an unused IP address in the same subnet as your router.  Let's assume your router uses 192.168.1.1.  Pick another address, say 192.168.1.237, and then run these commands from a terminal:
```

sudo ifconfig eth0 192.168.1.237 netmask 255.255.255.0 broadcast 192.168.1.255
sudo ip route add default 192.168.1.1
ping -c 5 192.168.1.1
ping -c 5 8.8.8.8

```
Replace the IP addresses with the correct ones given your router's configuration.  Most home routers use 192.168.1.0/24 or 192.168.0.0/24 by default.  Can you now ping the router at 192.168.1.1?  How about Google's DNS server at 8.8.8.8?  If both those work, you should be able to upgrade.  If you have a problem with DNS, report back, and I'll suggest a workaround.

Another option is to try resetting KDE to its defaults by renaming .kde in your home directory to .kde.old, then logging out and logging back in.  In Dolphin, you'll need to hit Alt+period to display "hidden" files like .kde, or select the appropriate entry from the Control menu (the one with the gear) at the top.

---

### Post by morgenstern2 on 2014-04-23
Thx for the answer; are you sure i can upgrade my OS without a working internet connection? I would love to do it, but it seems complicated to me... :)

Renaming .kde is a workaround that already saved my life many times, do you think it could help with this specific issue?

---

### Post by SeijiSensei on 2014-04-23
> **morgenstern2 said:**
> Thx for the answer; are you sure i can upgrade my OS without a working internet connection? I would love to do it, but it seems complicated to me... :)

I added some material in about that, probably while you were replying.  It's not really that complicated.  Just a couple of terminal commands.

> Renaming .kde is a workaround that already saved my life many times, do you think it could help with this specific issue?

It might.  In ~/.kde/share/config/ I have a networkmanagementrc which contains a couple of basic configuration entires, and there's a ~/.kde/share/apps/networkmanagementrc/ directory with additional stuff.  

Another option may be to remove the existing network manager applications from the system tray and reinstall it again.  To do this, right-click the existing icon, choose Panel Options > Panel Settings.  The panel will expand.  You should now be able to right-click the networking icon and choose "Remove". Then use "Add Widgets" to restore it.  I don't know whether this will remove the underlying misconfiguration though.

---

### Post by vajorie on 2014-04-23
> **morgenstern2 said:**
> Thx for the answer; are you sure i can upgrade my OS without a working internet connection? I would love to do it, but it seems complicated to me... :)

To be honest, I wouldn't deal with the upgrade at this stage, especially since you don't have a network connection + network-manager crapped out like this. Since 13.10 support ends soon, it would be just much more easier and quicker to grab an iso for 14.04, backup your personal files, and install a *fresh* k/ubuntu. In fact, as you get the iso and boot to the **live system**, you can test whether 14.04 has the same issue in your case, and if it does, see if another distro solves it for you. That would also allow you to see if this is a driver issue. 

> Renaming .kde is a workaround that already saved my life many times, do you think it could help with this specific issue?

I don't have KDE so I don't know whether any NetworkManager settings are kept under .kde. I doubt it does. You could always try and see, since if it doesn't help, you can simply move your .kde.old back to .kde. 

I wonder if there is any interesting info in the output of `dmesg' and in the logs /var/log/syslog. You could check the configuration files under /etc/NetworkManager/ and /var/lib/NetworkManager/ to see if something looks wrong there. (God knows why its files are spread out like that, eesh.) More specifically[1], the /etc/NetworkManager/nm-system-settings.conf (I think that's what it's called? Currently away from my computer.) file should read like
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

```
and the /var/lib/NetworkManager/NetworkManager.state file should read
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true 

```

[1] Source (it's old but it makes sense): [http://ubuntuforums.org/showthread.php?t=1451064](http://ubuntuforums.org/showthread.php?t=1451064)

---

### Post by morgenstern2 on 2014-04-23
[                                                      **@**]("http://ubuntuforums.org/member.php?u=698195")[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")

"Replace the IP addresses with the correct ones given your router's configuration" Sorry, how do i know router's configuration?

Anyway i tried with the commands you suggested, this is what i get

First command: no output, so it's fine
Second command: *Error: either "to" is a dublicate, or "192.168.1.1" is a garbage*
Third command: it works fine, packets are transmitted
Fourth command: doesn't work, i get *command: Network is unrechable*

I tried to rename .kde but it didn't help... the funny thing is that with the new .kde i couldn't even see the network manager in the tray and no network manager application was found in the programs...

Removing and re-adding the windget in the panel didn't help either...

---

### Post by SeijiSensei on 2014-04-23
Sorry, I left out the keyword "via" in the route command.  Try this:
```
sudo ip route add default via 192.168.1.1
```
Since the first command worked (in that it didn't throw an error), once the route is set correctly you should be able to ping the Google server and run "sudo do-release-upgrade".

It looks like your router is configured to use 192.168.1.x since it didn't complain, and you can ping 192.168.1.1.

---

### Post by morgenstern2 on 2014-04-23
@Seiji The last command you suggested me worked fine and i could ping google properly.

Instead, checking for the new ubuntu release says "no new release found"

It seems strange to me...

Actually, as the connection works, can i surf the internet somehow?

---

### Post by morgenstern2 on 2014-04-23
@[**[COLOR=#000000]vajorie[/COLOR]**]("http://ubuntuforums.org/member.php?u=603583")

Thx for your help and suggstions.

Unfortunatly, in my situation getting a new ISO wouldn't be so easy: finding a way to print a new DVD etc; more, i would prefer not to reinstal everything (even if of course it would the final solution if anything else works).

There are so many infos on the /var/log/syslog i wouldn't know where to start the checking from; next time i rebbot my computer i will try to tell you more.

I found that thread you link me some hours ago and i used it to create the nm-system-settings.conf (i didn't have any). So now this file is fine.

Concerning the other one, the strange thing is that everything seems to be fine but i have one more line: "WWANEnabled=true". Can this be an issue?

---

### Post by SeijiSensei on 2014-04-23
Yes, you're fully connected to the Internet now.

Here are detailed instructions for upgrading from 13.10 to 14.04:  [https://help.ubuntu.com/community/TrustyUpgrades/Kubuntu](https://help.ubuntu.com/community/TrustyUpgrades/Kubuntu)

Perhaps the problem was that 13.10 was itself not up to date.

---

### Post by SeijiSensei on 2014-04-23
> **morgenstern2 said:**
> @Seiji The last command you suggested me worked fine and i could ping google properly.

Instead, checking for the new ubuntu release says "no new release found"

It seems strange to me...

Actually, as the connection works, can i surf the internet somehow?

Yes, you're fully connected to the Internet now.

Here are detailed instructions for upgrading from 13.10 to 14.04:  [https://help.ubuntu.com/community/TrustyUpgrades/Kubuntu](https://help.ubuntu.com/community/TrustyUpgrades/Kubuntu)

Perhaps the problem was that 13.10 was itself not up to date.

---

### Post by morgenstern2 on 2014-04-23
Sorry, it's my fault; i was too happy and i didn't properly check the  google ping: it says 100% packet loss... And i'm not surfing... :(

---

### Post by SeijiSensei on 2014-04-23
But you can ping the router successfully?

Try turning off the power to the router, then wait fifteen seconds and plug it back in.  Any better?

---

### Post by SeijiSensei on 2014-04-23
But you can ping the router successfully?

Try unplugging the power from the router, then wait fifteen seconds and plug it back in.  Any better?

On one of the other machines that works correctly, let's check its network settings.  On an Ubuntu machine, run the commands "ifconfig" and "route -n".  You should see an ifconfig entry for either eth0 or wlan0 that has an address.  The route command should point the default address, which may appear as 0.0.0.0, to your router as I indicated above.  On a Windows machine, go to Start > Run, and type "cmd" into the box.  You'll get a terminal window.  Type "ipconfig /all" and look at the results to see what IP address and gateway the machine has.  

Now rerun the ipconfig/route commands I gave you earlier with new IP addresses that have the same initial three numbers as the working examples.  Make sure the gateway address is the same as on the other machines, but choose an IP address for the non-working machine that ends in a number between 1 and 254 that is not being used by another computer on the network.

---

### Post by morgenstern2 on 2014-04-24
ifconfig on a windows xp (yes, windows xp!) computer gets

```
Microsoft Windows XP [Versione 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\alberto>ipconfig /all

Configurazione IP di Windows

        Nome host . . . . . . . . . . . . . . : soggiorno
        Suffisso DNS primario  . . . . . . .  :
        Tipo nodo . . . . . . . . .  : Sconosciuto
        Routing IP abilitato. . . . . . . . . : No
        Proxy WINS abilitato . . . . . . . .  : No
        Elenco di ricerca suffissi DNS. . . . : homenet.telecomitalia.it

Scheda Ethernet Connessione alla rete locale (LAN):

        Suffisso DNS specifico per connessione: homenet.telecomitalia.it
        Descrizione . . . . . . . . . . . . . : ASUSTeK/Broadcom 440x 10/100 Int
egrated Controller
        Indirizzo fisico. . . . . . . . . . . : 00-E0-18-B4-63-04
        DHCP abilitato. . . . . . . . . . . . : Sì
        Configurazione automatica abilitata   : Sì
        Indirizzo IP. . . . . . . . . . . . . : 192.168.1.45
        Subnet mask . . . . . . . . . . . . . : 255.255.255.0
        Gateway predefinito . . . . . . . . . : 192.168.1.1
        Server DHCP . . . . . . . . . . . . . : 192.168.1.1
        Server DNS . . . . . . . . . . . . .  : 192.168.1.1
        Lease ottenuto. . . . . . . . . . . . : giovedì 24 aprile 2014 10.23.27
        Scadenza lease . . . . . . . . . . .  : giovedì 24 aprile 2014 16.23.27

Scheda PPP alberto:

        Suffisso DNS specifico per connessione:
        Descrizione . . . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Indirizzo fisico. . . . . . . . . . . : 00-53-45-00-00-00
        DHCP abilitato. . . . . . . . . . . . : No
        Indirizzo IP. . . . . . . . . . . . . : 151.16.25.49
        Subnet mask . . . . . . . . . . . . . : 255.255.255.255
        Gateway predefinito . . . . . . . . . : 151.16.25.49
        Server DNS . . . . . . . . . . . . .  : 193.70.152.15
                                            212.52.97.15
        NetBIOS su TCPIP. . . . . . : Disabilitato

```

(it's in italian, but i hope you can understand the main infos)


Shutting on and off the computer didn't help.

I modified the commands you suggested me as follows

```

sudo ifconfig eth0 192.168.1.62 netmask 255.255.255.0 broadcast 192.168.1.255
sudo ip route add default 192.168.1.62
ping -c 5 192.168.1.62
ping -c 5 8.8.8.8

```

The results are the same as before: I can ping the router but not google. For google i get "Destination Host unrecheable"

---

### Post by SeijiSensei on 2014-04-24
The computer you showed us has a PPP connection with a public Internet address of 151.16.25.49 as well as its 192.168.1.45 address on your network.  The PPP address usually means you have some type of dialup Internet connection. Yet that machine also reports that 192.168.1.1 is its default gateway.  So I'm rather confused about how you are connected to the Internet.  I'm guessing that you must have some type of router at 192.168.1.1, and that that is your main connection to the Internet.

If so, then the route command ought to point the default to 192.168.1.1 as we did before.  That router device is the one I wanted you to "power-cycle," not one of the computers behind it.

However, if your actual connection to the Internet goes through the machine with the PPP connection, then try using its IP address, 192.168.1.45, as the default gateway in the route command rather than 192.168.1.1.

It would help if you described your local network arrangement in more detail; in particular how is your home connected to the Internet?  Is it the PPP connection we just saw, or is there another device connected to a DSL or other type of connection?

---

### Post by morgenstern2 on 2014-04-24
Thx for be so kind and patient!

I'm not sure about the technical details of this network; there is a router (or a modem? I never really understood the difference) and four computers connected with ethernet cables. For contract reasons no more then two can be connected at the same time.

From each computer, to connect, you have to set a DSL connection with the same username and password.

Now I'm writing from the computer whose NetworkManager under Kubuntu doesn't work; i just installed Lubuntu on a another partition and connection works. So it's really a configuration problem.


Here is the output of the commands you suggested me before from this computer; i hope it can help.
```
silvia@michael:~$ ifconfig
eth0      Link encap:Ethernet  IndirizzoHW bc:ae:c5:a0:69:77  
          indirizzo inet6: fe80::beae:c5ff:fea0:6977/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4932 errors:0 dropped:1 overruns:0 frame:0
          TX packets:3635 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:5416650 (5.4 MB)  Byte TX:507459 (507.4 KB)
          Interrupt:50 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:735 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:67133 (67.1 KB)  Byte TX:67133 (67.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          indirizzo inet:151.16.26.101  P-t-P:151.23.224.84  Maschera:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3543 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:3 
          Byte RX:5300264 (5.3 MB)  Byte TX:425758 (425.7 KB)

wlan0     Link encap:Ethernet  IndirizzoHW 74:2f:68:87:97:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

silvia@michael:~$ route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         151.23.224.84   0.0.0.0         UG    0      0        0 ppp0
151.23.224.84   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0


```

---

### Post by morgenstern2 on 2014-04-24
If it can help, here are the outputs of some logs i collected after rebooting on kubuntu

$ sudo cat /var/log/syslog | grep NetworkManager
[http://pastebin.ca/2702261](http://pastebin.ca/2702261)

$ dmesg
[http://pastebin.ca/2702264](http://pastebin.ca/2702264)

---

### Post by morgenstern2 on 2014-04-27
A friend of mine found out that i probably had a bridged pppoe connection and thus suggested me the following commands: 

$ sudo pppoeconf


$ sudo pon dsl-provider


Worked fine for me!

---

### Post by morgenstern2 on 2014-04-27
How can i add [SOLVED] to the thread name?

---

### Post by Iowan on 2014-04-27
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

