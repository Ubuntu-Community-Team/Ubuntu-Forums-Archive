---
title: "[SOLVED] networking not working"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by Curious65 on 2008-02-07
first thanks to any and all help. also i've searched and read <strike>all</strike> a bunch of  threads about networking but none have addressed this problem.

i have three computers running right now. two with Ubuntu 7.10 an a XP Pro box. I'm using smb for the network interface. i can ping all of them from here and the other linux box. i can see the shared folders on the windows box when i click MyToys (name of Windows network) but when i click the MSHOME (Linux network) icon all i get are the shared folders for that particular computer. 

maybe this flow thingy will exlain the problem. network>shared folder and Windows Network>mshome and my toys

from my toys>xp computer>shared folders

from mshome>shared folders that computer only.

---

### Post by bwhite82 on 2008-02-07
Its been a while, but I seem to recall that when doing this, all computers need to be on the same share-domain (ie MSHOME). Try making the network name the same on all computers. I could be wrong on that though.

---

### Post by Curious65 on 2008-02-07
that would explain the windows box not seeing linux since it's different domains but not the two linux boxes problem.

---

### Post by Iowan on 2008-02-07
Another possibility... Samba client comes pre-installed on Ubuntu, but Samba Server does not(?).  That might explain why the Linux boxes can see the Windows share, but not vice-versa.

---

### Post by Curious65 on 2008-02-07
if by Samba Server you mean the app that installs with "share this folder" then it's now on /in here. i'm not concerned about seeing linux from windows as much as seeing both linux boxes. 

i have the "mshome" domain but clicking it in either linix box doesn't open up the other.

---

### Post by Iowan on 2008-02-07
Yes... that's the one I meant.   Now I'm a bit bewildered, but wonder if one of the boxes needs to be set up as master browser. A section of my server's /etc/samba/smb.cfg file:```

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true
   os level = 100
   domain logons = yes
 [COLOR="Red"]  preferred master = yes[/COLOR]
   passdb backend = tdbsam guest

```

---

### Post by Curious65 on 2008-02-07
navigated to the file you posted and it looks nothing like yours:

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

it's quite obvious i don't know enough about all this stuff yet and will have to do a lot more reading in the samba-doc package before i can either figure it out or ask the right question. what's driving me crazy is that all the help files (and some of the online help and user posts) make it sound like what i've done so far should work. oh well.

thanks for your help.

---

### Post by lansalot on 2008-02-08
Try this from the command line on each:

ps -ef|grep mbd

You should see an smbd and a nmbd process running. Then, from each, try:

smbclient -L \\\\other_box_name

(if name resolution isn't working, then try adding -I other_box_ip_address)

Browser master shouldn't be an issue immediately, as by negotiation one machine will have already assumed that role. If one of your linux boxes is on more often than the XP box however, you are as well making that your master browser, so read up in the samba docs on how to do that.

Better off having them all in the same workgroup however, so in the smb.conf's, put:
workgroup = MyToys

---

### Post by bigken on 2008-02-08
try this 

sudo apt-get install samba 

sudo apt-get smbpasswd -a (your name)

sudo apt-get smbpasswd -e (your name)

 sudo /etc/init.d/samba restart

good luck :)

---

### Post by swerdna on 2008-02-08
> **Curious65 said:**
> navigated to the file you posted and it looks nothing like yours:

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

it's quite obvious i don't know enough about all this stuff yet and will have to do a lot more reading in the samba-doc package before i can either figure it out or ask the right question. what's driving me crazy is that all the help files (and some of the online help and user posts) make it sound like what i've done so far should work. oh well.

thanks for your help.

If that's your file smb.conf then your Samba networking can't work. You need to install the original default  for smb.conf and start fromn that. I've attached a copy for you to install over the file /etc/samba/smb.conf.

Then if you want to get your network going you need to change a few lines to make the default smb.conf compatible with LAN workgroups. Open smb.conf  for editing with terminal command **sudo gedit /etc/samba/smb.conf**. Change the workgroup name fromn "WORKGROUP" to the windows workgroup name (MyToys I think).
Decide what network name you want for the computer (for arguments sake suppose it's computa_name) and add this line under the line "workgroup = MyToys": **netbios name = computa_name**.
Now change this line which is not right for a LAN workgroup: **;   name resolve order = lmhosts host wins bcast**
To this line which is right: **name resolve order = bcast host wins  lmhosts**. NB to remove the leading semicolon.

Then if the Linux machines are similarly configured, but with differtent netbios names, you should see only the one networking workgroup, after you reboot the network machines.

And there are by default no shares on the Linux machines. So if you want some, describe what they should do and I'll show you what to add to the files smb.conf on the Linux boxes to achieve the shares. Or maybe you wish to use one of the three sharing GUI devices in Ubuntu.

Swerdna

---

### Post by Curious65 on 2008-02-08
first thanks to [lansalot, bigken] and [Swerdna] for your replies. please excuse the delayed response, RL called.

re shares. i have some done with the GUI and they are there on both machines, just not visible to each other.

[Swerdna] i can't open the attached file. get a dialog box saying it's .txt and to change my preferences. if i knew how or where i would :) it may also be an error since i seem to be getting errors on the page right now.

am going to read up on samba-doc and with that, all your help and maybe osmosis this will sink in. don't have a lot of time this weekend but will post a followup when this is resolved.

---

### Post by Curious65 on 2008-02-08
**Swerdna** just FYI i rebooted which cleared up my browser problem and downloaded the .txt file. after a cursory glance it looks a lot like my current etc/samba/smb.conf file with the notable exception of the domain name in global settings.

---

### Post by swerdna on 2008-02-09
> **Curious65 said:**
> **Swerdna** just FYI i rebooted which cleared up my browser problem and downloaded the .txt file. after a cursory glance it looks a lot like my current etc/samba/smb.conf file with the notable exception of the domain name in global settings.
Sorry, I thought you posted your real, actual smb.conf. In any event, you need to add not only workgroup = whatever but also netbios name = .... and name resolve order, if you wish for good network.
Good luck
Swerdna

---

### Post by Curious65 on 2008-02-09
hi **Swerdna** if you are really bored i have attached my actual smb.conf file to this post. went to /etc/samba/smb.conf and copied the file into an open office document. i had to cut out the leading text, the section on authentification, debugging and mounting the CD drive to get to the 19.5kb file size limit.  

there are parts of it at the bottom that look like windows .ini files. those are in the "share definitions" and actually the first encompasses both the second and third.

about the time i think it all makes sense then another section contradicts what i thought. but i'll preserve.

---

### Post by swerdna on 2008-02-10
> **Curious65 said:**
> hi **Swerdna** if you are really bored i have attached my actual smb.conf file to this post. went to /etc/samba/smb.conf and copied the file into an open office document. i had to cut out the leading text, the section on authentification, debugging and mounting the CD drive to get to the 19.5kb file size limit.  

there are parts of it at the bottom that look like windows .ini files. those are in the "share definitions" and actually the first encompasses both the second and third.

about the time i think it all makes sense then another section contradicts what i thought. but i'll preserve.

Here's a cleaned up version if you want one. The shares [Pictures] and [Shared] are superfluous so you can delete them if you wish or alternatively delete [dave] (or keep them all - won't hurt).

Make proper netbios name -- most peole just use the Linux hostname (it's in the prompt) but can use just about anything.

If you use this -- KEEP a copy of the working version in case this doesn't work. Reboot or **sudo /etc/init.d/samba restart**

```
[global]
        workgroup = MSHOME
        server string = ""
	netbios name = ****whatever********
	passdb backend = tdbsam
	socket options = TCP_NODELAY IPTOS_LOWDELAY
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	name resolve order = bcast host lmhosts wins

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[dave] 
	path = /home/dave 
	public = yes 
	writable = yes
	force user = dave 
	
[Pictures] 
	path = /home/dave/Pictures 
	public = yes 
	writable = yes
	force user = dave 
	
[Shared] 
	path = /home/dave/Desktop/Shared 
	public = yes 
	writable = yes
	force user = dave
```

Swerdna

---

### Post by Curious65 on 2008-02-10
thanks for the cleaned up version. don't have time to try it today but will as soon as i can and post the results.

have yours and mine side by side on the screen and when you say "cleaned up" you're not kidding. :) however by seeing yours a lot of what i've read makes sense now.

---

### Post by Curious65 on 2008-02-10
well it's not as you might have done it **Swerdna** but it's working. ending up using the network settings at system/administration/network settings/wired network/general tab to change the host name and put that new host into the mshome domain. 

then i tweaked the permissions until i got something that will work for me. screwed that up more than once, even to the point of getting an error message at boot login regarding 644 permissions that i had to google. 

at this point i can see an image file (for example) on the network in linux1 and copy it but then have to paste it unto linux2 outside of the network. get an "access denied" error trying to navigate back through the network to paste it. but that's ok because i can at least see the darned thing now.

my printers are physically connected to linux2 and a print command sent from linux1 doesn't generate an actual print output. the printer installed and is seen but somewhere the path is wrong. that's for another day and with your smb.conf file as a guide i'll figure it out. 

thanks again for all your help and the help from the others who posted answers.

---

