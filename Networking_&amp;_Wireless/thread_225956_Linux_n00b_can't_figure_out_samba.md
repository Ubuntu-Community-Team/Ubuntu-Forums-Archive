---
title: "Linux n00b can't figure out samba"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by POKETNRJSH on 2006-07-30
Hey, I just got this linbox up and I want to network with my winbox. I tried using the samba documentation and I can see my shared drive in my winbox, which is online, but when I try to connect to it with samba using "smb://winjosh/" it times out. What do I need to do on this box to connect?

---

### Post by x64Jimbo on 2006-07-30
Let Windows Filesharing through in your windows firewall. It's likely blocked right now.

---

### Post by POKETNRJSH on 2006-07-30
It's going through on that end.

---

### Post by x64Jimbo on 2006-07-30
Not sure what you mean by that.

---

### Post by POKETNRJSH on 2006-07-30
Sorry; I meant that I have an unobstructed connection on my winbox. I have this feeling that I need to do something on this end, but I have no idea what.

---

### Post by x64Jimbo on 2006-07-30
You have unobstructed connection from your winbox to your Linux box? That makes sense. You still need to let Windows FIlesharing through on your firewall if you want INCOMING connections to work, not just outgoing.

---

### Post by POKETNRJSH on 2006-07-30
Alright, I went in and allowed all operating system components on tcp/udp and now I can get to my drive in samba. Is there a specific program I'd want to allow? This seems like it might be a bit unsafe to allow all of them.

Also, for the exception I put in, I can specify an IP address. I would enter the IP of this box, correct?

---

### Post by x64Jimbo on 2006-07-30
There's normally a checkbox that says "Windows File Sharing" 
If you allow ONLY that one, you should be OK.

---

### Post by POKETNRJSH on 2006-07-30
I don't see one specifically for that, but there's some for other connections and whatnot. Perhaps there's a different name? I have PC-Cillin, if that makes a difference.

edit: I switched to the office profile and it still seems to be working.

---

### Post by x64Jimbo on 2006-07-30
Ok, then that's the difference. The built-in Windows firewall calls it by its real name. If you can add apps by port, you can add 445. That's the windows file sharing port.

---

