---
title: "Open Ports = Security Problem?"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Toronto11 on 2010-12-05
Hi everyone, 

I'm new to Ubuntu and am curious to know how secure it is.  Do I need anti-virus, a firewall, and I'm not too sure about ports?  Do I want them open or closed?  I'd like my system to be as secure as possible.

I have port scanners from the synaptic package manager downloaded, but I don't know how to run them.

Thanks for the help.

---

### Post by Frogs Hair on 2010-12-05
Ubuntu has a built in firewall that is set to deny by default  , if you would like a simple GUI for setting port rules install Firewall Configuration from the software center and you can find it on the administration menu post installation.

If you are worried about sending infected files to Widows users there is antivirus for Linux . Clam tk , Avast and AVG  are three that I know of.

I have never tried the scanners that you wrote about , but read the post in the link before you decide what security measures you take.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by dacanadianbomb on 2010-12-05
That is a good link previously provided and should answer most questions.

I personally use clamav-daemon (apt-get install clamav-daemon) and clamtk (apt-get install clamtk) , coupled with rkhunter (apt-get install rkhunter), and do weekly scans after making sure the definition files are updated.

If you are looking for a simple firewall GUI, I use gufw (apt-get install gufw ).It interfaces with "ufw" and ufw by default when enabled is set deny all incoming whilst allowing all outgoing.

I would suggest you review what you are planning on doing with your machine.
Once you know what you will want to do with the system you can assess what dangers your machine may be exposed to based on that and choose mitigations to those risks.

---

### Post by mcduck on 2010-12-05
> **Frogs Hair said:**
> Ubuntu has a built in firewall that is set to deny by default  , if you would like a simple GUI for setting port rules install Firewall Configuration from the software center and you can find it on the administration menu post installation.

If you are worried about sending infected files to Widows users there is antivirus for Linux . Clam tk , Avast and AVG  are three that I know of.

I have never tried the scanners that you wrote about , but read the post in the link before you decide what security measures you take.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Actually no, Linux does have built-in tools for creating firewalls, and ubuntu comes with a configuration tool included, but it isn't even enabled by default. it doesn't have to be, since there are no running processes that would listen for incoming network connections, and thus there is nothing for a firewall to block.

You'll only need a firewall if you install some application that does listen for incoming network connections, like some server application for example. And even then you'll usually either want the server to be accessible from network, or can configure the server itself to only accept desired connections or connections from local network or localhost only.

If you still think you need a firewall, you can either use the included command-line tool [UFW]("https://help.ubuntu.com/community/UFW") to enable it, or install the graphical frontend Gufw from repositories.

edit: port scanners would require you to run the scan from a remote machine, running one on the system you want to scan is pretty much pointless. But unless you have installed any servers on your Ubuntu system, you'll have no open ports so no need for any scanning.

What comes to antivirus, there really isn't much for one to scan either. You might want to consider one if someday somebody makes a Linux virus that actually spreads in the wild (and doesn't require you to install and run it manually or have a certain server app version that's outdated by couple of years or something :D). For now, the antivirus apps available for Linux will just search for Windows viruses. Usefull for a corporate mail server, for example, but there's little need for such thing on a home Linux system. (people often make the point that you might accidentally give a virus-infected file to your Windows-using friend, but I'd say if that Windows user's antivirus can't handle it he's already in some serious trouble anyway and probably has gathered a couple of viruses from the Net already... ;))

---

### Post by MrWES on 2010-12-05
> **Toronto11 said:**
> Hi everyone, 

I'm new to Ubuntu and am curious to know how secure it is.  Do I need anti-virus, a firewall, and I'm not too sure about ports?  Do I want them open or closed?  I'd like my system to be as secure as possible.

I have port scanners from the synaptic package manager downloaded, but I don't know how to run them.

Thanks for the help.

You can conduct a port scan at Shields Up!

[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Bill

---

