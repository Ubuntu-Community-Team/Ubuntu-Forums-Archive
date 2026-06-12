---
title: "Samba - user security w/out Ubuntu Accounts"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by AndyInNYC on 2010-08-06
I have a slew of Windows PC users who will need to access my Samba Server.  I want to have the following conditions, but I'm having no luck:

1.  user/group level security - I must be able to firewall off certain portions
2.  I will not know in advance what the 'PC Name'/'PC login' name of the users may be on their PC.
3.  I'm fine with the users being required to login to the share with a username and password
4.  For 'known' users, I'm fine with them having a useradd account on the linux box if necessary, but I  don't want it to show up as a choice on the login screen (I think I know how to fix this one).  I should be able to create the mappping for these known users.
5.  I'd like all users who have access to a directory/file to be able to edit/read/delete/make a subdirectory, etc. (I know this is the mask, but 0775 probably isn't my best choice - although I think it works)
6.  Users don't need/get a home directory (yet)

Box is 10.04 64 bit server with GUI and fully patched.

I could post my various smb.conf's, but I'm too far off.

process I've tried:

create a user on the Ubuntu box w/out login:
     useradd -c "Alice Jones" -M -s /sbin/nologin alice
create a samba user
     smbpasswd -a alice

in the smb.conf file, I have:
     valid users = x,y, alice 
I have tried this as x y alice (without the commas)

From the PC, I try to map the drive to:
\\ServerName\Share
using "different login name" which is alice and alice's password

clearly I'm missing something!!!

Any thoughts?

Andrew

---

### Post by cariboo on 2010-08-07
I would suggest you have a look at [Samba 3 By Example]("http://www.samba.org/samba/docs/man/Samba-Guide/") it walks you through setting up varous sized networks.

I would also suggest you disable the gui, and only use it when needed. Remove GDM, and start the gui at the prompt by typing:

```
startx
```

You can also use X-forwarding with ssh. Install openssh-server, it is in the repositories, and when you need to use a gui app, ssh into the server using the following command:

```
ssh -X user@server
```

Then type the name of the app at the prompt, if you need to use the file manager type:

```
nautilus
```

For a howto have a look [here]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html").

---

### Post by AndyInNYC on 2010-08-07
Thanks for the reply.

I have examined various websites and guides; unfortunately it just isn't working for me <insert frown here>.

I'm trying not to read a book now to adjust 3 lines of a .conf file, though.  I'm not a sys-admin and don't really want to be.  I would just like to get this configured and *then* spend time reading and tinkering around and increasing my level of knowledge.

I don't understand why you'd suggest I disable the GUI - it provides value.  Again, I don't want to learn sometimes cryptic commands for things that I may look at only once or twice a year.  I'm neither that dedicated nor do I have that level of recall any longer <insert second frown!>.

I think your response got cut off since your howto reference didn't refer to anything.

Andrew

---

