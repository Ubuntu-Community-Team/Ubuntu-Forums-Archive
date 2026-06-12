---
title: "Ubuntu 9 file server and WinXP clients"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by herewasplato on 2009-10-01
I have a fresh installation of Ubuntu 9.04 (U9) desktop acting as a file server for 30+ WinXP Pro (XP) boxes.

Some XP boxes connects via their own unique user name and password using...
net use Z: \\U9\share /USER:user password /PERSISTENT:YES
...to map the the U9 share.

Other XP boxes connect as guest (without getting prompted for name/pswd). Guests have read only access to the shared files.

This is working as desired, except restarting any XP box causes it to reconnect the mapped drive as a guest.


smb.conf contains only this:

[global]
workgroup = xxxxxxx
server string = ""
dns proxy = no

security = share
guest = nobody

encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes

[Userdata]
path = /media/x/share
username = @group1 @group2
read only = no
guest ok = yes


Any suggestions as to how I can prevent the XP restart = guest access?

If I must, I can use a batch file during start up to...
net use Z: /delete
net use Z: \\U9\share /USER:user password /PERSISTENT:YES
...but the timing of that gets messy.


Thanks for your time.

---

### Post by boblemur on 2009-10-01
hey there are 2 things you can try:

1) try mounting it from the gui, tools > mount network drive if i remember correctly.

2) disable simple file sharing (i dont know why but this causes alot of issues sometimes).


im pretty sure that this is a windows based config problem not ubuntu, id say your samba is working fine.

---

### Post by herewasplato on 2009-10-03
Thanks for your quick reply.

The computer gods have blessed me with a hardware failure.

When it gets fixed or replaced... "**I'll be back**" :: best Schwarzenegger voice.

Or for you older folks - "**I shall return**."

Thanks again.

---

### Post by boblemur on 2009-10-03
lol ok, well im subscribed to this post so when you get it fixed repost here, and i will see that you've responded, so untill then :) cyaz

---

### Post by herewasplato on 2009-10-05
Okay - new box - same setup as mentioned in the first post.

Using Tools > Map Network Drive... on the XP clients never prompts for a user ID and password - so it logs me on as guest and read-only.

I do want guest users to connect without being prompted for a password...
but I want those that map a drive via  "net use" to have their authentication (permission level) survive a reboot.

Perhaps I want too much :-(

---

### Post by boblemur on 2009-10-06
> **herewasplato said:**
> Okay - new box - same setup as mentioned in the first post.

Using Tools > Map Network Drive... on the XP clients never prompts for a user ID and password - so it logs me on as guest and read-only.

there is a little link on the dialog where it says "connect as different user" or something similar to that, try that for adding a username/password

> **herewasplato said:**
> Perhaps I want too much :-(

never :) u use ubuntu now... theres always a way.


so first try to mount though the gui as that may do it. also turn of simple file sharing (As that sometimes causes problems)

---

### Post by herewasplato on 2009-10-06
Sadly, doing the steps that you mentioned did not help XP reconnect after a restart and keep the correct user level privileges. Then it dawned on my to try the area where XP "**keeps**" passwords to a server...
[IMG]http://i35.tinypic.com/xgdzck.png[/IMG]
...but that too failed until I tried the computername/username format as shown above.

**~~~I sure wish ideas would come into my head in the correct order~~~**


Thanks for your help/time.

P.S. Testing was done using a XP Pro within a Virtual Machine. After each test, the VM was reset to a state that had no "knowledge" of previous connectivity attempts.

---

