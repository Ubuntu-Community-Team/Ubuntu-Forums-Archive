---
title: "Filesharing in 8.10 Ibex"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by sERAPHIM_newbie_at_linux on 2009-02-18
Hi all,

After trawling through these forums looking how to file share with my Windows box, with limited to success, I came across a simple explanation of how to get a Samba GUI and use that instead (see link below).

(Don't get me wrong, use command line following these forums, I did manage to get filesharing up at one stage, but then I still couldn't write to Ubuntu box from Windows box)

For other Ubuntu newbies who want to learn more command line stuff, I recommend using the GUI as instructed in the below link, and then check your smb.conf file (sudo gedit /etc/samba/smb.conf) to see what the GUI has done.

Anyways, here is the link:
[http://geekdomain.wordpress.com/2008/12/29/sharing-files-between-windows-and-linux-xp-vista-ubuntu/](http://geekdomain.wordpress.com/2008/12/29/sharing-files-between-windows-and-linux-xp-vista-ubuntu/)

---

### Post by sERAPHIM_newbie_at_linux on 2009-02-18
Continuing on from my above post, I also have a QUESTION!!

I want to make it so only I can access my Ubuntu box via fileshare. So I want to be able to go to Network Connections in Windows (XP) and click on the Ubuntu share (I chose /home/nath/public) and have it bring up a login box.

This much I HAVE managed (though I'll be darned if I can remember how). BUT when I tried to log in, no name and password combination would work. In the Samba GUI I set it to USER authentication, the guest account was 'nath' (what I login to Ubuntu with) and password was set to encrypted. I then made a Samba user under my 'nath' Ubuntu account and set my Windows login to 'Nath' (my account in windows, duh) and I set the samba password for that user to the same password I use for both my 'nath' and 'Nath' accounts. Just to make sure, I did command line smbpasswd nath, and entered in my desired password; and I checked smbusers and surely enough there was nath=Nath.

So, on my understanding when I double click the 'Public' folder in Windows's Network Connections, it should bring up a log in. I should then enter Nath, which Samba will associate with my Unix account nath, and my samba password. Then it should give me access to that folder, with the same permissions as the Unix nath account.

So why is this not working? Can somebody please explain in simple this-guy-is-a-linux-dumbass language how to do what I'm trying to.

Thanks so much :)

---

### Post by sERAPHIM_newbie_at_linux on 2009-02-22
Hi hi,

Can nobody help me?!? :(

---

### Post by pdtpatrick on 2009-02-22
[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

### Post by sERAPHIM_newbie_at_linux on 2009-03-15
Sorry, but that link didn't give me the answer I needed at all. Plus it gave a totally different scenario - namely setting up a standalone server. 

So... BUMP!

---

### Post by hyper_ch on 2009-03-15
actually, that link gives you all the information you need.

---

### Post by MrWES on 2009-03-15
goto your home folder via nautilus (file manager for Ubuntu); navigate the folder you want to share and click the right mouse button; sharing options. If the required software is not installed, ubuntu will install it. There is an option for whether or not you want to share with others.

Bill

---

### Post by sERAPHIM_newbie_at_linux on 2009-03-29
@everyone
Apologies for the faux-bump by responding to hyper and MrWES

@hyper
alright, thanks. I'll have to have a better look at the article then, when I get more time. At the moment, my Windows box has a corrupt HDD anyway, so I can't test out my Samba sharing until its back in action.

@MrWES
Thankyou for trying to offer support, I do appreciate that. But if you read my original posts more carefully, you'll see I do understand how to make basic filesharing happen. What I am after is a password-on-request scenario.

Let me quickly explain again - Im on Windows XP, I go to Network Connections. I click on Samba share (located on Ubuntu box). It opens. INSTEAD, I want it to request a username and password, (which actually works instead of rejecting all possible responses), and then opens.

---

