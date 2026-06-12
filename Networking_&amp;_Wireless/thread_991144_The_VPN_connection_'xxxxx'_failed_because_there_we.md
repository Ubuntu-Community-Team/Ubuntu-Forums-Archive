---
title: "The VPN connection 'xxxxx' failed because there were no valid VPN secrets."
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by giesen2 on 2008-11-23
Brand new install of Ubuntu 8.10 (Intrepid Ibex). I installed network-manager-pptp through Synaptic and did a full restart.

I'm trying to get a VPN connection setup. This is a standard windows VPN host

The VPN connection 'xxxxx' failed because there were no valid VPN secrets.

I've googled this error, and tried several suggestions of switching authentication options, but nothing is working.

How do I get the detailed logs regarding this error?

Thanks!

---

### Post by Iowan on 2008-11-24
HAve you seen [this]("https://help.ubuntu.com/community/VPNClient") VPN Client Help page?

---

### Post by slacker9876 on 2008-11-24
I was having the same problem and I used this method:


[Solution Source]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503")

Hi -
 Here's how to get it working in Ubuntu Intrepid for a Windows home network. Before trying this, be sure your router allows PPTP service.
 Open Network Configuration (Start, System, Preferences).
Highlight your VPN connection, hit Edit.
At IPv4 Settings Tab: choose method Automatic (VPN).
At VPN Tab:
1 - input the IP address of the target computer.
2 - input your user name.  Leave all else blank.
3 - hit Advanced button.
At Authentication:
1 - UNcheck PAP (because PAP means to allow unsecured passage - this is the source of "no shared shared secrets")
2 - Check CHAP, MSCHAP and MSCHAPv2.
At Security and Compression:
1 - Check Use Point-to-point encryption (MPPE)
2 - Select 128-bit (most secure).
3 - Check Allow stateful encryption.
At Echo:  check Allow PPP echo packets.
Leave all else blank.  Hit OK, OK to save and get out.
 Note:  Your password is requested on VPN startup.  I did not try to add it to the keyring.


This worked for me but no until I removed my password from the actual connection. I am on my VPN right now. I hope this helps.

---

### Post by Black Serpent on 2008-11-30
I think I solved the problem.

The source of the problem is - the application nm-pptp-auth-dialog wants to access the keyring to search for the password.

The problem: there is no such record in the keyring table. so it returns an error. **Due to a bug, the application do not append the record in the first place!**

solution:

make a new VPN connection. Connect to it. Click Deny when prompted: "Allow application to access keyring?"

then enter the password manually, and check "Save password in keyring"

then click Allow Always

and Wallah, you have just created the required entry in the keyring! You'll no longer have "no secerts" problem!

(goto applications > accessories > keyring manager > passwords to see it!)

Hope this helps. Please let me know if it doesn't.

---

### Post by bastett on 2008-12-01
Thanks Serpent,
this worked for me too.

Has this been lodged as a bug?

---

### Post by Black Serpent on 2008-12-02
my pleasure!

I don't know. should I report it as a bug?

---

### Post by mothman7 on 2009-06-24
AHHH this is such an annoying error. Unfortunately, none of the info I could find online really fixes it. You can connect if you do not store your password in the key ring, but if you get disconnected, you have to do it all over again every time. 

However, I found a real solution. Uninstall the Gnome Network Manager applet and install the KDE one instead. The bug in in the Gnome applet. The KDE applet also works with Gnome, so you don't need to run KDE. If you need PPTP install Kvpnc as well. I am successfully running both with Gnome, configured them to use PPTP and it worked on the first try, no more errors. It uses the KDE keyring and remembers your password as well. 

This is a serious bug that needs to be fixed, fortunately KDE can save you here.

---

### Post by mac666 on 2009-08-20
Any news? Is this bug fixed? Can only find KVpnc KDE and i cant handle it...

---

### Post by abasco on 2009-09-14
> **slacker9876 said:**
> I was having the same problem and I used this method:


[Solution Source]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48503")

Hi -
 Here's how to get it working in Ubuntu Intrepid for a Windows home network. Before trying this, be sure your router allows PPTP service.
 Open Network Configuration (Start, System, Preferences).
Highlight your VPN connection, hit Edit.
At IPv4 Settings Tab: choose method Automatic (VPN).
At VPN Tab:
1 - input the IP address of the target computer.
2 - input your user name.  Leave all else blank.
3 - hit Advanced button.
At Authentication:
1 - UNcheck PAP (because PAP means to allow unsecured passage - this is the source of "no shared shared secrets")
2 - Check CHAP, MSCHAP and MSCHAPv2.
At Security and Compression:
1 - Check Use Point-to-point encryption (MPPE)
2 - Select 128-bit (most secure).
3 - Check Allow stateful encryption.
At Echo:  check Allow PPP echo packets.
Leave all else blank.  Hit OK, OK to save and get out.
 Note:  Your password is requested on VPN startup.  I did not try to add it to the keyring.


This worked for me but no until I removed my password from the actual connection. I am on my VPN right now. I hope this helps.

Hi, I have similar problem, how do I find out if my router allows PPTP service?

---

### Post by azredwing on 2009-10-14
> **Black Serpent said:**
> I think I solved the problem.

The source of the problem is - the application nm-pptp-auth-dialog wants to access the keyring to search for the password.

The problem: there is no such record in the keyring table. so it returns an error. **Due to a bug, the application do not append the record in the first place!**

solution:

make a new VPN connection. Connect to it. Click Deny when prompted: "Allow application to access keyring?"

then enter the password manually, and check "Save password in keyring"

then click Allow Always

and Wallah, you have just created the required entry in the keyring! You'll no longer have "no secerts" problem!

(goto applications > accessories > keyring manager > passwords to see it!)

Hope this helps. Please let me know if it doesn't.

Verifying that this method works; I can connect to my vpn server now. Running Jaunty x64.

---

### Post by rtobyr on 2009-10-19
I ran into this problem because I'd put in my Windows Active Directory domain name into the "domain" field in the network manager's VPN wizard thing. In my environment, we're using RADIUS to authenticate VPN such that the username and password is always the same as what it is on MS AD. I solved the problem by clearing the "domain" field.

---

### Post by mstjohn1974 on 2009-10-27
I am using Ubuntu too and connect to a Windows VPN Network... try my instruction at [http://mstjohn1974.blogspot.com](http://mstjohn1974.blogspot.com)

I hope it helps

---

### Post by T3kG33k on 2009-11-05
What if you're unable to get the VPN service to start?

---

### Post by Joel Duckworth on 2010-11-21
If you get this with Maverick 10.10. Try just rebooting and connecting again, seems something is screwy after you install the package and haven't rebooted yet. Maybe a logout/in would work too, let us know.

---

### Post by ptipton on 2010-12-01
> **Joel Duckworth said:**
> If you get this with Maverick 10.10. Try just rebooting and connecting again, seems something is screwy after you install the package and haven't rebooted yet. Maybe a logout/in would work too, let us know.

Rebooting worked a treat for me in 10.10

---

### Post by Dimath on 2010-12-03
> **ptipton said:**
> Rebooting worked a treat for me in 10.10

Although it is a shame for a linux, I confirm that reboot helps in Ubuntu 10.10

---

### Post by LaPalida on 2010-12-04
Confirming that the reboot fixed the problem for me on Maverick 10.10.

---

### Post by Hiroaki on 2010-12-19
I can confirm that reset works, but is unnecessary.  I simply did:
```
sudo restart network-manager
sudo /etc/init.d/networking restart
```I'm not sure which of the two (or if both) did the trick, as I did both in sequence without testing.  Also, I have no idea why network-manager is available to upstart but not networking...weird.  Anyway, to whomever stumbles across this, don't waste those precious seconds rebooting (and that inevitable minute or two to remember what all you had open).

---

### Post by raztus on 2011-01-20
Thanks, Hiroaki!  You've saved me a few precious seconds.  I used the first of your two commands and it worked:

[INDENT][FONT="Courier New"]sudo restart network-manager[/FONT][/INDENT]

---

### Post by ultimatewarrior on 2011-03-03
I'm running ubuntu 10.10, and It seems that restarting is still not doing the trick .

The network manager applet is saying cannot connect because VPN service failed to start, however tail -f +10 /var/log/syslog is telling me no valid VPN Secrets.

I've rebooted, tried creating new connections and restarting the network services to no avail.

---

### Post by matutet on 2011-03-31
Hi!,

I had the same problem and the solution for me was enable the "Available to all users" option in the Network Manager config.

Ugly :( but works :)

I'hope it will be useful for you.

Best regards.

---

### Post by afspear on 2011-08-23
> **raztus said:**
> Thanks, Hiroaki!  You've saved me a few precious seconds.  I used the first of your two commands and it worked:

[INDENT][FONT="Courier New"]sudo restart network-manager[/FONT][/INDENT]

This worked for me in 11.04

---

### Post by devin.fee on 2011-09-12
> sudo restart network-manager

works for me on 10.10. Thanks!

---

### Post by yjlego on 2011-11-21
> **ptipton said:**
> Rebooting worked a treat for me in 10.10

A simple rebooting of your system will do. Works for me~

---

