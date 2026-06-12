---
title: "Please explain simple folder sharing?"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by kcy29581 on 2008-07-13
Hi all,

I have tried searching the forums, Google, etc. I just want to know how to configure two Ubuntu machines to share folders, in Ubuntu 8.04 (Hardy Heron). Both machines have 8.04 installed.

Before anyone attempts to answer, please bear in mind that 8.04 has introduced a "Sharing Options" right-click option in Nautilus. If this is what needs to be used, please explain fully (for example, do not just say "create SAMBA users" if that is needed; say **how** I can create the SAMBA users).

Thanks, and I seriously hope someone can help with this.

---

### Post by goexplode on 2008-07-13
If you only want to share files between two Ubuntu machines, with no Windows machines involved, then I'd recommend using NFS.

[Here]("http://ubuntuforums.org/showthread.php?t=249889") is one really good tutorial that I was able to find here on the forums.

[Here]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html") is another good tutorial that I was able to come up with by simply Googling "ubuntu nfs tutorial."

---

### Post by kcy29581 on 2008-07-13
So what is the purpose of the "Sharing Options" right-click option in Nautilus?

Also, is there a GUI for NFS or am I asking for too much?

---

### Post by goexplode on 2008-07-13
> So what is the purpose of the "Sharing Options" right-click option in Nautilus?

I think it is an attempt at making sharing folders a little more accessible to the user using samba. Personally, I have never been able to get it to work properly in Ubuntu. I have always edited /etc/samba/smb.conf to set up everything how I need it since the GUI in Nautilus is fairly new and doesn't offer enough options to suit my needs.

> Also, is there a GUI for NFS or am I asking for too much?

I'm not sure if there is a good GUI for NFS in Ubuntu. Try searching the repositories for NFS and see what you can find. I know that Fedora/Red Hat offers a NFS GUI, but I'm pretty sure it is Fedora/Red Hat specific.

I'm not really too fond of using GUIs whenever it comes to configuring these types of things. But then again, I've been working with Linux and Unix systems for quite a while now. :guitar:

---

### Post by kcy29581 on 2008-07-13
I think I'm getting somewhere with SAMBA. I installed system-sonfig-samba (the app that the devs removed from Hardy) and it looks like it works much better that the incredibly broken "Sharing Options" option. I can see my shares on all machines. I just need to set up users but it looks fairly easy.

Thanks for the help. I just really want to find the dev that thinks that networking in Ubuntu works... I might just give up on Launchpad and Brainstorm as no one in the dev team cares. Just reading the responses reminds me of all the crappy dev teams in my company that enjoy making up excuses...

---

