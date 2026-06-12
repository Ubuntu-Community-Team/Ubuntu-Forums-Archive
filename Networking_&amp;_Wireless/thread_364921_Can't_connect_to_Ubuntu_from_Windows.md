---
title: "Can't connect to Ubuntu from Windows"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by NorgeNerd on 2007-02-18
I've been trying now for many hours to connect up to my Ubuntu machine from my Windows 2000 and my Mac machines, without success.   I'm new to Ubuntu & Linux, but not to computers & networking, so this is a bit on the frustrating side.  I've always been able to make connections from the Ubuntu workstation, but there is no reciprocity. I've installed Firestarter (as recommended in the desktop manual), and fooled with it endlessly, and edited the smb.cnf file over and over.  *Nothing ever changes*.  If firestarter is running, I get a "Network path not found" message when I click on the name of my Ubuntu machine from my Windows machine.  If I stop Firstarter, I at least get a logon prompt.  But my credentials are rejected (over and over).  

Thanks for your help.

---

### Post by mistypotato on 2007-02-18
I set up accounts on all computers with the same credentials.

For example, I have the same username and password on the Ubuntu (Samba) machine as I do on the WindowsXP machine.

Also, they are all in the same workgroup.

---

### Post by NorgeNerd on 2007-02-19
Check--We're all in the same workgroup & I've got the same credentials on both machines.  I really wish that was all I needed.  I've seen a lot about WINS servers in this forum, so I've fiddled with that a lot.  Nothing makes the slightest difference--except stopping Firestarter (but even that change doesn't allow a connection to happen).

---

### Post by gradedcheese on 2007-02-19
have you added your user(s) via smbpasswd?  If not, then it won't work until you do.  You can skim through my [short guide about it]("http://andrey.thedotcommune.com/samba.html") or at least do this:

```

sudo smbpasswd your_user_name
sudo /etc/init.d/samba restart

```

---

### Post by NorgeNerd on 2007-02-21
Thanks so much.  Funny that None of the stuff I've read so far (a considerable amount) mentioned this.  

I can't try this right at the moment, but will definitely let you know how it comes out.

Thanks again.

---

### Post by gradedcheese on 2007-02-21
yeah, it's kind of a problem that this isn't made clear :(

I am starting to work on a patch for the Shared Folders tool that will make this happen automatically (and improve things in other ways), so hopefully this won't be an issue if/when I succeed with that.

---

### Post by looping_richard on 2007-02-21
Hello,
thanks for the solution regarding the smbpasswd.
It worked for me.
This should really really be in a much more accessible place... the Shared Folders was where I was looking for the password settings. No such thing there :(


Thanks again,
Richard.

---

### Post by NorgeNerd on 2007-02-23
Pretty satisfying to see those Linux shares pop up on my PC.  Thanks so much.  Your instructions were so clear and precise that everything worked right out of the box.  Sounds like you're a Ubuntu developer.  Very happy to have made your acquaintance.

---

### Post by gradedcheese on 2007-02-23
You're very welcome.  I'm not an Ubuntu developer (I'm an embedded systems guy) but I am going to try and work on some Gnome pieces (namely making samba configuration more automatic).

---

### Post by neopsalmist on 2007-11-10
this was very helpful, but I can't link to your "short article". 
Thanks

---

### Post by HermanAB on 2007-11-10
BTW, if you really want to know how to configure Samba, then you should read John Terpstra's Official Howto on the Samba web site.

Cheers,

Herman

---

