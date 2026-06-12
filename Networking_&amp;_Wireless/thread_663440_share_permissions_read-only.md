---
title: "share permissions read-only??"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by Gwaihirjp on 2008-01-10
Hello!! I'm experiencing a rather inconvenient problem right now with the share on my Ubuntu server and I'm hoping that someone can help me out with this one.

On the network there are about 10 windows boxes connected to one Ubuntu Samba server. There is one shared folder, called "Public", and I want each Windows box to have read/write access to all the files inside that Public folder.  
Every user in the network has been added as a Samba user, and they are all in one group, called "autocomjapan", and according to what I see on my settings, everyone should be having read-write access. It works at first, when the file has just been put on the server.

But here is where the problem starts. When someone opens and edits the file, that file becomes his/hers, and everyone else on the group gets read-only access until that "owner" edits the permission for the group. Even the administrator account on the server has no permission to edit a file after it's been edited by someone-else. When that new "owner" gives read/write permission to the group, it stays that way until the next person opens and edits it (then that next person becomes owner).

When I look at my Smb.conf, this is what I get for that folder:
> [Public]
	path = /home/autocomjapan/Public

;	browseable = yes
;	available = yes

	writeable = yes
	valid users = autocomjapan, fujimura, fukai, ikuno, imamura, naito, okazawa, sangin, taisia, takesue, tsubaki, urata


This is not good because the people using Windows boxes keep complaining about not being able to edit the files. Please someone help!

---

### Post by gazj on 2008-01-10
try adding this line to your share

force group = @autocomjapan

---

### Post by Gwaihirjp on 2008-01-10
Thank you for your reply, Gazj. I tried adding that line to the smb.conf like you suggested, but it seems like the Windows boxes cannot open the Public folder when the "force group" line is there... instead, a popup appears saying something like "cannot find group name".

---

### Post by gazj on 2008-01-11
[http://www.linuxquestions.org/questions/linux-software-2/samba-permission-for-sharing-public-and-private-folder-478264/](http://www.linuxquestions.org/questions/linux-software-2/samba-permission-for-sharing-public-and-private-folder-478264/)

Maybe this will be o some help, sounds similar to what you are trying to achieve.

---

### Post by Gwaihirjp on 2008-01-14
Thanks, I'll try that later today when I get the time. I'm wondering though, what does the "force group" do? I googled it a bit and couldn't really find the answer.

---

