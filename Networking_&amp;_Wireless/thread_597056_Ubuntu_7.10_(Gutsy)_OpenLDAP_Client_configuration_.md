---
title: "Ubuntu 7.10 (Gutsy) OpenLDAP Client configuration guide"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by kesomir on 2007-10-30
I know what a pain ldap setup can be in ubuntu, and as I have now solved most of the deal breakers I thought I'd share this information in the hope that others will find it useful (I know I would have). Perhaps if we can get the TLS changes in from someone who uses that, this can be complete. Be nice to have this up on the wiki. 

Please point out errors, omissions and improvements.

**[CENTER]This guide is for authenticating GUTSY (7.10) against an OpenLDAP directory server in a linux network[/CENTER]**

Ensure all your repositories are set up via "software sources" in admin or pointing towards your local apt cache (apt-cacher rocks btw as it only caches what you download and keeps only the most recent versions rathet than requiring a complete mirror) manually.

Open a terminal window
Authenticate as root (you can alternatively precede all commands with sudo if you wish) and make sure everything is up to date.

```
sudo su
aptitude update
aptitude upgrade
```

[SIZE="4"]
[B]Ubuntu NFS client setup
[/B][/SIZE]

```
aptitude install nfs-common portmap
```

nano /etc/fstab

add the lines

```

#this line for the home dir
SERVER_IP:/export/users /home/users nfs rw,rsize=32768,wsize=32768,hard,intr,timeo=14,bg
#this line for all additional mount points except /etc/skel
SERVER_IP:/export/FOLDERNAME /media/LOCALFOLDER nfs rw,rsize=32768,wsize=32768,hard,intr,timeo=14,bg
```

for each of your nfs mount points as configured on your nfs server. I use nfs mounted home directories and a selection of others in media for staff, students and office. I used to mount /etc/skel as well, but I don't anymore.

One problem I have is that clients sometimes do not mount the NFS shares on bootup depending on network load (I think), which then doesn't allow login if the home is one not mounted (my ldap users home is at /home/users/dir/u-name).

[SIZE="4"]
[B]Ubuntu OpenLDAP client authentication (No TLS).
[/B][/SIZE]

Install the ldap required packages

```
aptitude install auth-client-config libpam-ldap libnss-ldap
```

A configuration screen will appear:
```

Should use debconf -> YES
URI -> ldapi:///LDAP_SERVER_IP
DISTINGUISHED NAME -> dc=localdomain,dc=local
LDAP VERS -> 3
LOCAL ROOT DB ADMIN -> YES
DOES DB REQ LOGIN -> NO
LDAP A/C -> cn=admin,dc=localdomain,dc=local
LDAP root a/c password -> PASSWORD
```

My understanding is that this should configure the /etc/ldap.conf file which now acts as central control. However, it doesn't work ;)

so...

```
nano /etc/ldap.conf
```

change:

```
host 127.0.0.1
```

to

```
host LDAP_SERVER_IP
```

```
base = padl....
```

to

```
base = dc=localdomain,dc=local
```

uncomment 

```
bind_policy=hard 
```

and change to 

```
bind_policy=soft
```

Now, because there is another ldap.conf in /etc/ldap/ldap.conf I duplicated it

```
cp /etc/ldap/ldap.conf /etc/ldap/ldap.conf.bak
cp /etc/ldap.conf /etc/ldap/ldap.conf
```

Now for the use of auth-client-config (instead of the more laborious manual editing of the pam files):

Create a new ldap profile:

```
nano /etc/auth-client-config/profile.d/open_ldap
```

and paste this into it

```
[open_ldap]
nss_passwd=passwd: ldap files
nss_group=group: ldap files
nss_shadow=shadow: ldap files
pam_auth=auth       required     pam_env.so
        auth       sufficient   pam_unix.so likeauth nullok
        auth       sufficient   pam_ldap.so use_first_pass
        auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
        account    sufficient   pam_ldap.so
        account    required     pam_deny.so
pam_password=password   sufficient   pam_unix.so nullok md5 shadow use_authtok
        password   sufficient   pam_ldap.so use_first_pass
        password   required     pam_deny.so
pam_session=session    required     pam_limits.so
        session    required     pam_mkhomedir.so skel=/etc/skel/
        session    required     pam_unix.so
        session    optional     pam_ldap.so




```

This is an improvement on the default ldap setup because it will create a home directory if one doesn't exist on login. I authenticate ldap before files because in order to access usb sticks the "on the fly" assignment method doesn't work. To fix this, an ldap user in the plugdev group is used.

Then execute this to enable the above config:

```
auth-client-config -a -p open_ldap
```

Now for on the fly group assignment for all users on login paste:

```
auth    optional        pam_group.so
```

Into the top of both /etc/pam.d/gdm AND /etc/pam.d/login. it's important to place it first as these files are not parsed once a sufficient / required is met.

```
nano /etc/security/group.conf
```

paste into the top:

```
login;*;*;Al0000-2400;users,cdrom,floppy,plugdev,audio,dip
kdm;*;*;Al0000-2400;users,cdrom,floppy,plugdev,audio,dip,video
gdm;*;*;Al0000-2400;users,cdrom,floppy,plugdev,audio,dip,video
```

This is the part that assigns all users logging in to the users, cdrom, floppy, plugdev (broken for HAL), audio, dip and video groups.

Now create a group in ldap called plugdev and assign it the gid 46. This will allow usb sticks etc to be mounted as an ldap user assigned to the group.

---

### Post by alessice on 2007-11-02
Your post was very very usefull for me.

I have migrated my users from files to ldap with migratetools and now i manage LDAP users with webmin!

Thank you!

---

### Post by kesomir on 2007-11-06
I recommend using Gosa2 to manage ldap users - v nice if using open ldap.

---

### Post by jirihnidek on 2007-11-07
Hi,
your article was very useful for me too, but I'm not able to create group plugdev in LDAP server, because I'm not LDAP admin and LDAP admin is against adding such group to LDAP (it isn't systematic solution :-) ). btw: I use university LDAP with 10 000 users in this LDAP. Could I solve this problem with usb stick in different way?

Thanks

---

### Post by AgentZ86 on 2007-11-08
I already have a LDAP server setup with SME server, but can't seem to use the LDAP address book portion of Evolution for some reason. It does not allow me to select a LDAP, only selection is under the personal address book.

Please advise

---

### Post by Herrmannek on 2007-11-10
> **kesomir said:**
> 
Now, because there is another ldap.conf in /etc/ldap/ldap.conf I duplicated it

```
cp /etc/ldap/ldap.conf /etc/ldap/ldap.conf.bak
cp /etc/ldap.conf /etc/ldap/ldap.conf
```

AFAIR they are different config files.. the one that sits in /etc/ldap/ seems to be  used by ldap-utils(ldapmodify, ldapadd and ldapsearch commands.)  and is of different format( look at "man ldap.conf" to learn more )  than ldap.conf directly in /etc that is now used by nss or pam.

BTW nss and pam should make use of the /etc/ldap/ldap.conf file but it seems they expect it in /etc/openldap/... as the /etc/ldap.conf file states. Its important fact if you want to use ldaps(SSL/TLS encyption). 
```

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
#ssl start_tls
ssl on

# OpenLDAP SSL options
# Require and verify server certificate (yes/no)
# Default is to use libldap's default behavior, which can be configured in
# /etc/openldap/ldap.conf using the TLS_REQCERT setting.  The default for
# OpenLDAP 2.0 and earlier is "no", for 2.1 and later is "yes".
tls_checkpeer no



```

---

### Post by kesomir on 2007-11-10
> **jirihnidek said:**
> Hi,
your article was very useful for me too, but I'm not able to create group plugdev in LDAP server, because I'm not LDAP admin and LDAP admin is against adding such group to LDAP (it isn't systematic solution :-) ). btw: I use university LDAP with 10 000 users in this LDAP. Could I solve this problem with usb stick in different way?

Thanks

No, it's a dirty, dirty workaround. However, since I and others have been sitting on a reported, triaged bug since edgy, I'm just glad to have working usb sticks.

(We think it's HAL btw).

Only other way I know around it is to switch to a LOCAL user to access the media. And yes, I tried a lot of different tricks on the way. Let me know if you come across a better solution. I would recommend trying to play with udev rules.

---

### Post by process91 on 2007-11-14
Thank you for the post, this is obviously an area which is "broken" in Ubuntu Gutsy. I have a serious problem even though I have followed your instructions to the letter - 

First off, I think that the file /etc/ldap.conf can be edited by using the utility instead of doing it manually. It doesn't retain the settings when you put them in on the install, as you had described. However, if you run 

```
sudo dpkg-reconfigure ldap-auth-config
```

It does retain the settings the second time around, so that may be of help.

Now for my problem - I believe the client is recognizing the server because if I type
```
su username
```
it asks for a password, which to me indicates that it knows of the user. (If you type in a username that doesn't exist it will tell you that the user ID doesn't exist). Unfortunately after entering a password it did not log me in, it returned "su: Authentication failure". So I restarted the computer.

After restarting the computer I still could not log on using the LDAP user, so I logged on locally. After logging on I found that my network manager applet was gone! This is a wireless laptop, so I normally use the network manager applet to select the wireless network. Anyway, I plugged it in instead and it did connect but the network manager was still gone. Then I took a look at my /etc/network/interfaces file and it looked like this

```
auto lo
iface lo inet loopback
```

Which wasn't what it looked like before. I checked another network interfaces file and copied most of what I found there and restarted networking. When I tried to restart by hitting the shutdown button in the top right of the screen the computer took a very very long time to show the shutdown dialog (3+ minutes).

Any Ideas?

---

### Post by kesomir on 2007-11-17
type 

```
id username
```

to see a return for an ldap users groups etc.

or 

```
getent passwd
```

for a full list of all users *including those in ldap.

if you don't get the ldap users, that part is failing.

Reboot the machine in recovery mode and run the above commands to see if you can get info from the ldap server and then boot up normally, switch to another tty (Ctrl+Alt+F1) try to log in and then try the same commands. See if there is a difference.

(Ctrl+Alt+F7 to return to the GUI terminal)

If you can log in as ldap from the terminal, then it's a gnome / gui issue, which may be down to the home directory.

A few questions:
What environment are you in? 
What type of LDAP is your server running? 
Does the LDAP server use TLS? 
Do you mount NFS shares? 
Can you connect to the LDAP server using another client? (SUSE or Fedora perhaps)

The first place to look for answers is in your logs:

Open System->Administration->System Log as a priviledged user, or from the terminal 

var/log/auth.log <- This will give you information about the authentication.
syslog, user.log and messages might also give useful info.

---

### Post by Tuge on 2007-11-30
Is there anything new to this subject?? I have gutsy ltsp server running on our school and I'm eagerly waiting for a solution to only remaining problem (usb mounting with ad-users)...

---

### Post by kesomir on 2007-12-01
This issue is client side.

Are you not able to implement the workaround I mention in the first post regarding the ldap group?

Failing that you might consider using a different distro - neither open suse or fedora have the usb problem - it's a Debian thing™

---

### Post by alessice on 2007-12-13
Hello,

i have a problem with change password with this configuration on Ubuntu 7.10 LDAP client:

cbs@desk1:~$ passwd
Enter login(LDAP) password:
passwd: Impossibile ripristinare informazioni autenticazione
passwd: password unchanged
cbs@desk1:~$                

and in the auth.log:

Dec 13 10:50:06 desk1 passwd[10633]: pam_unix(passwd:chauthtok): user "cbs" does not exist in /etc/passwd
Dec 13 10:50:09 desk1 passwd[10633]: pam_unix(passwd:chauthtok): user "cbs" does not exist in /etc/passwd

Why?
Thanks

---

### Post by felucca on 2007-12-18
> **Herrmannek said:**
> AFAIR they are different config files.. the one that sits in /etc/ldap/ seems to be  used by ldap-utils(ldapmodify, ldapadd and ldapsearch commands.)  and is of different format( look at "man ldap.conf" to learn more )  than ldap.conf directly in /etc that is now used by nss or pam.

BTW nss and pam should make use of the /etc/ldap/ldap.conf file but it seems they expect it in /etc/openldap/... as the /etc/ldap.conf file states. Its important fact if you want to use ldaps(SSL/TLS encyption). 
```

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
#ssl start_tls
ssl on

# OpenLDAP SSL options
# Require and verify server certificate (yes/no)
# Default is to use libldap's default behavior, which can be configured in
# /etc/openldap/ldap.conf using the TLS_REQCERT setting.  The default for
# OpenLDAP 2.0 and earlier is "no", for 2.1 and later is "yes".
tls_checkpeer no



```
I was able to make TLS authentication work in my Gutsy.

in /etc/ldap.conf (which is used by the PAM), you can set tls_chekpeer to no have PAM refer to /etc/ldap/ldap.conf file for the location of the certificate file. Although it says it refers to /etc/openldap/ldap.conf, it does actually refer to /etc/ldap/ldap.conf. 

and yes, you shouldn't blindly copy /etc/ldap.conf to /etc/ldap/ldap.conf, because the syntax is different. The following is what I have in my /etc/ldap/ldap.conf

HOST            example.com
BASE            dc=example,dc=com
TLS_CACERT      /etc/ldap/cacerts/cacert.pem 
TLS_REQCERT     allow

I am sooooooooooooo happy to finally make it work! :)

---

### Post by tekknokrat on 2007-12-19
> **kesomir said:**
> I recommend using Gosa2 to manage ldap users - v nice if using open ldap.

how do you get gosa running in gutsy, the packages are broken because of wrong smarty path
do you have a fix?

---

### Post by kesomir on 2007-12-30
My LDAP server runs feisty atm. However, I'm due to move that functionality to a virtual image - I'll play with gutsy and see if I run into any trouble..

It's just a php application though, have you tried setting up a webserver and using the code direct from the site?

[http://oss.gonicus.de/](http://oss.gonicus.de/)

there's a guide for installing it by unpacking the tarball here:

[https://oss.gonicus.de/labs/gosa/wiki/InstallingGOsa](https://oss.gonicus.de/labs/gosa/wiki/InstallingGOsa)

it's the third set of instructions.

This may also be useful:

[http://lena.franken.de/ldap/installing_gosa_debian_sarge.html](http://lena.franken.de/ldap/installing_gosa_debian_sarge.html)

---

### Post by tekknokrat on 2007-12-30
I already opened a ticket for that issue was in no time closed from the authors.

[https://oss.gonicus.de/labs/gosa/ticket/306](https://oss.gonicus.de/labs/gosa/ticket/306)

Later on I didnt investigate further because i already managed everything from commandline - i need this always as a learningstep, however  ;) .
I also was getting afraid of the lots of gosa dependant ldap schemas. 
I have the feeling they will break compatibility, can you agree to that tell for what they are useful?

---

### Post by kesomir on 2008-01-01
nothing for me - I had to install the samba schema because of it and it just takes up space - so if you're running ok from the command line (or phpldapadmin) then I wouldn't bother. I did it because I was starting out and wanted something working - Gosa2 has a nice interface, even just for user management and I came across a guide that <almost> worked ;) 

It has decent integration for controlling a few other things though - environment, opengroupware, mail, intranet, phpgroupware, fax, phone and references. The schemas for these are optional, so I don't use them - none of the apps are in use on my network anyway. Just the samba that was a req.

I'm working on building a debian etch openldap  + kerberos + tls atm, and will cut out the samba schemas if I can get that working.  I'll post the guide ofc, I document everything as I go now, which makes it easier.

Then of course it's NFS4....

---

### Post by HornedBeast on 2008-01-29
I've followed the guide for giving everyone group permissions when they login. I copied the group scheme that my local default user has when I installed Ubuntu. I used:

```
id -G -n
``` to find out the names and just comma'ed them into /etc/security/group.conf.

This did seem to have some affect, as the restricted driver manager flashed up when I booted and things, but I still can't SUDO anything from any of my LDAP users logged in (into Gnome of course).

Any advice?

---

### Post by Termina on 2008-02-02
> **Tuge said:**
> Is there anything new to this subject?? I have gutsy ltsp server running on our school and I'm eagerly waiting for a solution to only remaining problem (usb mounting with ad-users)...

I'm interested in a solution to this as well. Why does this not work?

---

### Post by dumbo01 on 2008-02-04
> **tekknokrat said:**
> how do you get gosa running in gutsy, the packages are broken because of wrong smarty path
do you have a fix?


**Smarty Fix**

Edit *php_setup.inc* (usually found in /usr/share/gosa/include)

Change Line 245 From
```
ini_set("include_path", ".:$BASE_DIR/include");
```

To
```
ini_set("include_path", ".:$BASE_DIR/include:/usr/share/php");
```


Hope it helps.

---

### Post by cpthk on 2008-02-25
Can anyone tell me what is this guide for? From my view, it's for user log in to linux either from the same computer or login through network(telnet, SSH). And linux will authorize password through openLDAP instead of passwd original shipped. Can anyone confirm this?

Thanks.

---

### Post by HornedBeast on 2008-02-26
For a full configuration guide for LDAP, check this link here.

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Its for having one server with all the usernames, passwords and home folders on it - and allows you to login from any client machine and it authenticates your username and password against the server, rather than the local machine.

---

### Post by songshu on 2008-05-08
thanks for the guide,

it was the missing part for me to get something going

URI -> ldapi:///LDAP_SERVER_IP
is this a typo?
should be
URI -> ldapi://LDAP_SERVER_IP

---

