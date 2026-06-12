---
title: "sharing files with osx"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by fistuks on 2008-08-25
Hello,
I've tried posting it in a different section and no one answered.
I'm trying to share folders with my macbook.
any idea's how?

I'm kind of lost here... any help will be welcomed.

---

### Post by coffeecat on 2008-08-25
I have just successfully set up a share folder in Ubuntu 8.04 and accessed it from my Mac Mini and copied a file across. The secret magic ingredient is that you are using networking technology originally developed by Microsoft (hack, spit! :wink:)

Create the folder you want to share in your home folder. Right-click on it and select 'Sharing Options'. Choose which options you want (these can always be changed later) and 'Create Share'. Now open a terminal and type 'hostname' (no quotes) and return and make a note of the hostname of your Ubuntu computer. Let's assume this was 'ubuntu'.

Now an important step. If you've installed a graphical firewall configurator like Firestarter, make sure you open the ports for Samba (SMB) or switch the firewall off.

In MacOS choose Go > Connect to Server from the Finder Menu and type 'smb://ubuntu/' (no quotes, and use your computer's hostname, not 'ubuntu') in the Server Address field. Press return, put in the password if you set one up and a Finder window should open for your shared Ubuntu folder.

If you want to do it the other way around, you can set up a SMB/CIFS share in the Mac System Preferences utility and browse you way into it with smb://MacHostname/ from Nautilus. Again, check firewall rules if you can't connect.

When I first played with smb shares and my Mac I found a way of autodetecting them in MacOS without having to type 'smb://hostname/sharename' or whatever. Now I can't find how to do it. If anyone knows please do post the answer.

---

### Post by fistuks on 2008-08-25
The mac is givingme an error massage again.

my computer name is "fistuks-desktop"

in the connect to server i entered :"smb://fistuks-desktop"

and it gave me - "connection faild - the server may not exist or it is not operational at this time. check the server name or IP adress and your network connection and try again."

any clues what went wrong?

---

### Post by coffeecat on 2008-08-25
> **fistuks said:**
> any clues what went wrong?

This is almost always a firewall problem. Have you installed a third-party GUI firewall like Firestarter? If you haven't - **don't**. Firestarter is full of bugs and I wouldn't recommend it. If you have, switch it off and try again.

Also check your firewall setting in MacOS in System Preferences > Personal > Security > Firewall. Make sure you haven't blocked any incoming services.

I had Firestarter installed this morning. Even though I (apparently) allowed samba/SMB in firestarter, my Mac couldn't connect to my Ubuntu share. It would only do so once I had disabled the firewall entirely. I've since uninstalled Firestarter (and good riddance) and installed [Gufw]("http://gufw.tuxfamily.org/index.html"), a graphical frontend to ufw. At the moment that's disabled as well because I was having problems getting the Mac to recognise the Ubuntu share. That was solved with rebooting the Mac, and I have yet to play with various settings in Gufw. One thing for future consideration once you've got this going: I've noticed before (with my fileserver) that sometimes the Mac would fail to pick up a share that it had been connecting to OK just a little while before, and that a reboot was necessary to get it to do so again.

Other things to check: double-check you have typed your hostname in correctly. If all else fails, go into the web configuration interface of your router and see what IP address it has assigned your Ubuntu machine. Instead of using the hostname, try 'smb://192.168.1.70/' replacing 192.168.1.70 with whatever the correct IP address is.

And obviously - check there is a working connection between your Ubuntu machine and router. Apart from that I have no other ideas except to stress: this sort of problem is almost always a firewall configuration one.

Lastly - thanks for asking your question. It spurred me into giving Firestarter the proverbial and long-overdue boot.

---

### Post by fistuks on 2008-08-29
Well, thanks for the answer but, unfortunately for me it is probably not the answer as it is disabled on my mac and i did not installed any on my ubuntu.

When ever i connect it keeps telling my of error code 36....

I can't even do it the other way around ubuntu don't see the mac.

---

### Post by fistuks on 2008-08-29
Anyone?...

---

### Post by codfish45 on 2009-01-22
I'm having the same issue.  Samba, nfs, Appletalk/Netatalk, none of them seem to work.  I'm also having the problem with Ubuntu being unable to see the mac, and sometimes the mac won't see ubuntu.

However, the machines can ping each other just fine, so there's some hope...

---

