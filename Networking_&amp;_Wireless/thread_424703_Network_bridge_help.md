---
title: "Network bridge help?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by Naetholix on 2007-04-26
Hey, guys.

I just ran a fresh install of Ubuntu 7.04 off the live CD, and so far, everything's working great.

I've run into a little snag, though, in my little network I have set up.

Here's what I've got:

I have an Atheros AR5005G Wireless NIC which communicates with our wireless router upstairs; from this I get my internet.  I also have a Realtek RTL-8029(AS) Wired NIC which I have connected to a router using a simple Cat5 cable.  On the other side of this wired router is my modded xbox.

My current situation is this:  I have my wifi enabled and I get nice and clean internet and smb between my computer and our Windows computer upstairs.  BUT as soon as I enable my wired connection, my internet dies and it's as if I have no network at all.  Both cards set on DHCP.

Before, in the dark days which I shudder to think about (back when I had Windows XP), I had my two networks NOT bridged, but I enabled a "shared internet connection" on my wifi, thus enabling my xbox to have internet access and perfect SMB and ftp file sharing between my xbox and my computer.  I believe this act forced my LAN card to a static IP address.

I guess my question would be this: Is there a way for me to have both networks enabled and still have internet to my computer and for my xbox?  Would I need to bridge them, somehow?  If so, how would I do that?

Another comment is that I made sure that I have different IP's for each router to avoid conflicts on the network. (xxx.xxx.0.xxx and xxx.xxx.1.xxx)

All input and comments are greatly appreciated!

---

### Post by chili555 on 2007-04-27
I believe that Network Manager is installed by default in Feisty (7.04). What you describe is exactly what Network Manager is designed to do. From [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
> Network Manager aims for Network Connectivity which "Just Works". The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.I don't think NM anticipates bridging, in which you want and need *both* connections at the same time. You might try disabling it under System -> Preferences -> Sessions -> Startup Programs. Reboot and you will need to reconfigure your interfaces, since they are no longer being controlled by NM.

---

### Post by Naetholix on 2007-04-27
Well... my internet doesn't come from a wired connection.  The only thing connected with a cable, down here, is my Xbox -> Router <- Computer.  Our wireless router has the WAN connected to it, and that's where I get my internet.  I don't want any switching back and forth between the two connections, and having my computer fight over which one it gets internet from.  I'd like for internet to come through my wireless for use by my computer and my Xbox, which means my wired connection needs to be connected at the same time.  I guess my main issue is needing a shared intenet connection from my wifi to my comp and my wired NIC.

And my network is already under manual configuration.  It started like that after I installed it, methinks.

---

