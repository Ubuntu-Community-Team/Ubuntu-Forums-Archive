---
title: "HOWTO: Share Gutsy Files for Windows Machines"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Yfrwlf on 2007-11-18
Sharing files with Gutsy has never been easier!  Gutsy (and in my experience, other Samba machines such as our modded Xbox with Xbox Media Center) share files with other Gutsy machines with no problems as long as your file permissions are set to be writable/readable by "others".

The only problem remaining is that Windows machines cannot access Gutsy machines without a username and password like other Samba machines can (or, other Samba machines already are using some guest account that I don't know about).  Since I don't know the default user and password for this if there is one, these are instructions on how to make a valid user and password for Samba to make it work.  "yourusername" will be your system user that you use to log in.  Open a terminal and type in:```
sudo smbpasswd -x yourusername
```After putting in your system user's password, this command will delete your existing Samba user account, so if there was one, the unknown password will be wiped out along with the account.  Next, we create the same user again, but for security reasons do NOT make your Samba user's password the same as your system user's password:
```
sudo smbpasswd -a yourusername
```You can either hit enter twice for no password, or specify anything you want.  Windows machines will now be able to see your shares by providing your username and the password you gave Samba (or no password if that's what you gave it).  If you'd like to make the Samba user account be some other name other than your system username, you'll need to create a new user for your system in Users and Groups, and afterward you'll be able to modify that user's account in Samba following the same process as above.

If you are having problems with your Windows machine and cannot see any workgroups and such, or see the computer on your network, to temporarily overcome this you can access the Gutsy box directly by going to it's hostname or IP address by typing it into Explorer.

There are other ways, and some of them may be simpler.  If you know them, or know what the default username and password that Gutsy machines use to share files with no prompt for a password, please let me know!  Hope this helps someone.

---

### Post by zox on 2007-11-18
This is fantastic and to the point, however second command, gksu didn't work for me.
When I replaced gksu with sudo, it worked as advertised.

Thanks for great and easy tip=D>

---

### Post by acracker on 2007-11-18
Thanks, that worked great! After I did that I ran:
sudo /etc/init.d/samba restart
to restart the samba service and then the settings worked.

---

### Post by Dirty Ole on 2007-11-18
> **Yfrwlf said:**
> 

The only problem remaining is that Windows machines cannot access Gutsy machines without a username and password like other Samba machines can 

...

There are other ways, and some of them may be simpler.  If you know them, or know what the default username and password that Gutsy machines use to share files with no prompt for a password, please let me know!  Hope this helps someone.

You CAN let Windows machines access Samba Gutsy machines without a username and password.

You to set the security to share from user (edit in smb.conf) and add 'guest ok =yes' to the share details.

---

### Post by Yfrwlf on 2007-11-19
> **zox said:**
> This is fantastic and to the point, however second command, gksu didn't work for me.
When I replaced gksu with sudo, it worked as advertised.

Thanks for great and easy tip=D>

Grr, forgot to change that to sudo as well, thank you!  I've changed it now.  But yeah, use sudo instead of gksu, I thought it did basically the same thing as sudo but for some reason you need to put quotes around the command to use gksu, I guess the program doesn't allow more than one other parameter.

---

### Post by Yfrwlf on 2007-11-19
> **Dirty Ole said:**
> You CAN let Windows machines access Samba Gutsy machines without a username and password.

You to set the security to share from user (edit in smb.conf) and add 'guest ok =yes' to the share details.

You're right, thank you, though I didn't mention that method simply because both of these methods involve using the command line so are somewhat equal in "difficulty", but out of the two methods the one I listed still uses security, so if some nooblet tries my way and doesn't have a secured router or whatnot, their files will be safer from prying eyes, especially if the user shares out anything writeable. :)

---

### Post by Yfrwlf on 2007-11-19
> **acracker said:**
> Thanks, that worked great! After I did that I ran:
sudo /etc/init.d/samba restart
to restart the samba service and then the settings worked.

I didn't have to restart Samba in my case, any setting changes that I made to users took place immediately, so I'm confused as to why you had to do that, but glad you got it working. :)

---

