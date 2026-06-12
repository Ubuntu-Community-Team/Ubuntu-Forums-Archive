---
title: "Sharing with xp using samba"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by havedampton on 2007-12-14
I have a shared folder on my linux box that I'm trying to access from my xp laptop.  I can see the linux box (it's name is kit) in the windows workgroup along with the laptop - the linux box is labeled "kit server (Samba, Ubuntu) (kit)"

When I click to open the linux box, it asks for a user name and password, but I don't seem to see any password or user name set up on the linux box's shared folders settings, and all of the user name's and password's I've tried are not correct.

Any help is greatly appreciated.
thanks

---

### Post by HermanAB on 2007-12-14
Did you do 'smbpasswd -a' for each user?

---

### Post by Alt69 on 2007-12-16
The steps I took after getting the smb.conf configured and samba started were:

Step 1) created ubuntu user. i used the GUI to do this. 
 
Step 2) I then created smb users using

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

Note: make sure the your_username and password are the same as that created for the regular ubuntu login user created in Step 1.

Then I went to my XP laptop and navigated to the shared folder:

 - My Network Places -> Entire Nework - Microsoft Windows Network - "group name" -> "Shared folder "

You will be prompted for the user name and password. Enter it and you should be good to go.


I have had lots of help, and lots of practice. :)    Hope that helps.


cheers

---

