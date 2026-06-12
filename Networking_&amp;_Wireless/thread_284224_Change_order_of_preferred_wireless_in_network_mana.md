---
title: "Change order of preferred wireless in network manager"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by akniss on 2006-10-25
At my workplace, there are two possible wireless networks that I connect to.  When I am in my office (90% of the time) I have a wireless router setup, and would like to connect to that everytime it is available (Say, connection A).  However, when I move to another floor of the building for meetings, etc., there is another wireless connection that I use (Say, connection B), as I can no longer reach connection A originating from my office.  Now that I have manually connected to both, is there a way to tell networkmanager which I would prefer to connect to if both are available?  The problem is that while connection A is very strong when I am in my office, network manager still tries to connect to connection B which is very weak, and requires web authentication every time.  How do I tell network manager to connect to connection A *every time it is available*?

---

### Post by K0LO on 2006-10-28
I'd like to know how to control networkmanager **at all**. It seems to have a mind of its own and no configuration file that I can find, and very little documentation.

You can do what you are describing if you configure your wireless manually. I used to do it that way by editing the /etc/network/interfaces file and then installing something like wpa_supplicant to manage encrypted networks. However, the configuration files for wpa_supplicant are pretty obtuse and may take a while to figure out. But in the end I was able to specify which network should have priority and get automatic selection.

Networkmanager is supposed to do that but I'll be darned if I can figure out how to gain control over what it's doing. Does anybody know where to find out more information?

---

### Post by Linuturk on 2006-11-01
I'd like to know this info as well. I have two open networks at my apartment. One is provided by the apartments, and works fine. The other is a open linksys that doesn't have net access. It seems Network Manager connects to either or at random.

---

### Post by Macchi on 2006-11-06
Hello Ubuntu fellows!
I am also looking for the same type of solution for the NetworkManager.

And this is a SECURITY issue, since the network manager apparently connects to anything available at random, just like our colleague Linuturk mentions. Unfortunately I have some neighbors with completely open wireless networks  and sometimes the NM connects to them. This becomes a security problem for me since some of the email servers I have to access are not encrypted. 

MY REQUESTS FOR THE NETWORK MANAGER:
1)I would like to be able to blacklist some wireless networks 

2) I would like to add a preference or priority order for other networks. This would assure security and performance.

3) I need integration with ppp: Another issue with the NM appears while using my 3G card for internet access through the mobile networks. This requires further steering with some ppp scripts and setting priorities would avoid the need for any manual intervention.

4) I would like to trim the Firewalls. To complicate things further, I will have to consider different firewall settings for every network connection alternative. May be I should look again at laptop-net, since it can do this job. The problem is that the manual configuration is scattered through many text files and is boring to maintain. I am looking for the bes of both worlds with flexibility, easy configuration and security. I am sorry to remember that I can get that out of the box through the mainstream OS on the market, but not yet with my favorite Ubuntu. 


Shall we file in a bug or feature request? Maybe there is already something being done about it? Any Ideas?

---

### Post by setdosa on 2007-02-28
I feel the pain too. My Network Manager keeps connecting me to the free network everytime and I have to manually select my network which is very annoying.

---

### Post by bedake on 2007-03-18
I'm experiencing a similar problem.  I tried connecting to my neighbors secured wireless network on accident the other day, since then network manager will auto attempt to connect to that network on startup instead of my own.  Since that network is secured if I do not catch it at the right time I will fail to connect and then, for some reason, I'll be unable to connect at all to even my own network.


So is there anyway at all to edit the list of networks that it will connect to or some other work around that just stops it from attempting to connect to a specific network?

---

### Post by akniss on 2007-03-18
To remove a wireless network from the 'preferred' list:

Hit Alt + F2 to bring up the "Run Application" dialog, then type in gconf-editor into the box.  Hit Enter.

In the left pane, expand the arrows next to system > networking > wireless > networks

Select the wireless network you wish to remove.

In the right pane, right click on all lines and choose "Unset Key" from the menu that appears. (the lines should begin with something like bssids, essid, timestamp, we_cipher, etc. Once all the keys are unset, the wireless network should be removed from the list that NM will try and connect to.

---

### Post by nobodysbusiness on 2007-03-27
Works for me. Thanks a lot for the great tip. That was just what I needed to know.

---

### Post by j3r3miah on 2007-04-06
> **akniss said:**
> Hit Alt + F2 to bring up the "Run Application" dialog, then type in gconf-editor into the box.  Hit Enter.

In the left pane, expand the arrows next to system > networking > wireless > networks

What version of nm-applet are you running? I'm running nm-applet 0.6.3 on Xubuntu and I don't seem to have a networking section under system in gconf-editor. Strange. Where, then, are the settings for nm-applet?

---

### Post by akniss on 2007-04-06
> **j3r3miah said:**
> What version of nm-applet are you running? I'm running nm-applet 0.6.3 on Xubuntu and I don't seem to have a networking section under system in gconf-editor. Strange. Where, then, are the settings for nm-applet?

Using NM 0.6.3 on Ubuntu Edgy.  It probably has to do with Xubuntu.  Do you have gnome services enabled? or are you running pure XFCE?

---

### Post by j3r3miah on 2007-04-06
I do have gnome services enabled.

---

### Post by curtHendzell on 2007-04-14
> **j3r3miah said:**
> What version of nm-applet are you running? I'm running nm-applet 0.6.3 on Xubuntu and I don't seem to have a networking section under system in gconf-editor. Strange. Where, then, are the settings for nm-applet?

gconf-editor is for changing settings for gnome.  This might work if you have gnome set up on your machine.  Otherwise I doubt it.

---

### Post by tormaser on 2008-02-28
great, tanks for the help

---

