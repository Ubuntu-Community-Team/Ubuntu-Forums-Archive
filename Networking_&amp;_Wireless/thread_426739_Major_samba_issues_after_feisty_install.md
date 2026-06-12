---
title: "Major samba issues after feisty install"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by cmay4 on 2007-04-28
Samba has worked perfectly fine in my network environment over the past two versions of Ubuntu.  Then I upgraded to feisty a few days ago.  After the upgrade, my XP machines could no longer connect to the server.  I spent a while tweaking my configuration in Samba.  After not knowing what the problem was, I decided to start over.  I followed the instructions in the thread:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

And I ended up with the smb.conf below.  After restarting, I was now able to log onto the Samba shares.  However, it's REALLY slow.  I'm not talking a bit slow, but unusable slow.  It takes about 20-30 seconds to copy a 250k from the server to the WinXP desktop.

Again, this was all working without problem for years before the feisty upgrade, so there is nothing wrong with my network.

Does anyone have any ideas?  I'm not sure where to go from here...

Chuck

```
[global]
    ; General server settings
    netbios name = homer
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[public]
    path = /home/public
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = may
    force group = users
```

---

### Post by cmay4 on 2007-04-28
Hmmm...i tried scp'ing a file from the server to my XP box.  I was only getting 4k per second over a 100MB wired connection.  So apparently the fiesty upgrade messed up something else.  

Has anyone else seen something like this?  

One other question.  Is it possible to downgrade back to edgy?

---

### Post by jdunn on 2007-04-28
I'm having a similar problem.  In Dapper and Edgy, the samba client worked out-of-the-box and always allowed me to connect to a Winblows network.  I installed the samba server and had it running nicely too.  Then, I made a fresh install of Feisty and neither the client nor server allow me to connect.  I can't downgrade but I'm already regretting that I installed the new distro so soon.

---

### Post by Raptor Ramjet on 2007-04-29
I too am unable to use samba after upgrading to Feisty as samba seems fundamentally broken.  When I try to start the samba service via 

   sudo /etc/init.d/samba restart

I get the message saying the service is started "OK" but when I look in swat (or use "ps -A") the service isn't actually running.  Additionally when I try to use smbtree it shows that the machine is present but there is a message that it failed to connect to the local machine (127.0.0.1 - not suprising if samba isn't running).

Additionally when I try to use smbpasswd it dumps as follows:

   smbpasswd -a user_name

No builtin nor plugin backend for tdbsam guest found
PANIC (pid 5494): pdb_get_methods_reload: failed to get pdb methods for backend tdbsam guest

BACKTRACE: 7 stack frames:
 #0 smbpasswd(log_stack_trace+0x22) [0x8105f42]
 #1 smbpasswd(smb_panic+0x43) [0x8106023]
 #2 smbpasswd [0x80c86da]
 #3 smbpasswd(initialize_password_db+0xe) [0x80c872e]
 #4 smbpasswd(main+0x532) [0x807a342]
 #5 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d23ebc]
 #6 smbpasswd [0x80799a1]
smb_panic(): calling panic action [/usr/share/samba/panic-action 5494]
smb_panic(): action returned status 0
Aborted (core dumped)

Finally attempting to run smbclient also gives me errors (which  I suspect are again down to the fact tha samba isn't running)

   smbclient -d 3 //machine_name/samba

lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.100.23 bcast=192.168.100.255 nmask=255.255.255.0
Client started (version 3.0.24).
resolve_lmhosts: Attempting lmhosts lookup for name machine_name<0x20>
resolve_hosts: Attempting host lookup for name machine_name<0x20>
Connecting to 127.0.1.1 at port 445
error connecting to 127.0.1.1:445 (Connection refused)
Connecting to 127.0.1.1 at port 139
error connecting to 127.0.1.1:139 (Connection refused)
Error connecting to 127.0.1.1 (Connection refused)
Connection to machine_name failed

Obviously I've uninstalled and reinstalled samba, smbfs, smbclient, winbind, swat, netkit-inetd, tcpd et. but nothing gets samba working.

I've also had tremendous graphics problems with Feisty (which ended up with me having to reinstall as nobody answered my forum post - [http://ubuntuforums.org/showthread.php?t=416810](http://ubuntuforums.org/showthread.php?t=416810)) MP3 ripping refuses to work properly so all in all I'm not impressed with Feisty at all.  In fact I've had more problems with Feisty than with any other Ubuntu upgrade.

Ho hum...

---

### Post by Tulsapoke on 2007-04-29
Has this been reported as a bug anywhere?  I need this fixed ASAP as this is the main function of my Feisty desktop system and now it shares almost unusable.

---

### Post by ntetreau on 2007-04-29
Might not be the problem you are having, but I get the same output with smbpasswd has you do if I failed to use the sommand with sudo in front.  

```
smbpasswd -L -a user
```

output:

```

Failed to open /var/lib/samba/secrets.tdb
Failed to open /var/lib/samba/secrets.tdb
Failed to open /var/lib/samba/secrets.tdb
pdb_generate_sam_sid: Failed to store generated machine SID.
PANIC (pid 7811): Could not generate a machine SID

BACKTRACE: 6 stack frames:
 #0 smbpasswd(log_stack_trace+0x22) [0x8105f42]
 #1 smbpasswd(smb_panic+0x43) [0x8106023]
 #2 smbpasswd(get_global_sam_sid+0x1e7) [0x8089a87]
 #3 smbpasswd(main+0x53f) [0x807a34f]
 #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7c7eebc]
 #5 smbpasswd [0x80799a1]
smb_panic(): calling panic action [/usr/share/samba/panic-action 7811]
smb_panic(): action returned status 0
Aborted (core dumped)

```

When I use sudo, I get a prompt for the new password.

---

### Post by jdunn on 2007-04-29
There is this bug report.  Commenting out "msdfs proxy = yes/no" in smb.conf seems to fix the problem for alot of people.  It made no difference for me but, try it anyway.  Here's the link:  

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460)

---

### Post by cmay4 on 2007-04-29
Well, after much head scratching, my problem turned out to have nothing to do with Samba.  My router was flaking out.  After replacing it, my problems went away.  Looks like there are definitely issues though.  Thanks for you help,

Chuck

---

### Post by mordak13 on 2007-04-29
Well I used the above smb.conf file and now I can read and write to my Windows boxes from my Linux box but not the other way from Windows to Linux. I had it working before my upgrade to Feisty as well. It seems like maybe a permission issue. any ideas?

---

### Post by mordak13 on 2007-04-29
> **jdunn said:**
> There is this bug report.  Commenting out "msdfs proxy = yes/no" in smb.conf seems to fix the problem for alot of people.  It made no difference for me but, try it anyway.  Here's the link:  

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460)
Thanks jdunn for this info I will give it a try.

---

### Post by jdunn on 2007-04-29
> **mordak13 said:**
> Well I used the above smb.conf file and now I can read and write to my Windows boxes from my Linux box but not the other way from Windows to Linux. I had it working before my upgrade to Feisty as well. It seems like maybe a permission issue. any ideas?

I just tried the smb.conf file above too.  No luck, whatsoever.  My only saving grace is, I can ping the other box and vice versa.

---

### Post by mordak13 on 2007-04-29
I had success by commenting out the "msdfs proxy = yes/no" in smb.conf. Thanks again for the info. \\:D/

---

### Post by jdunn on 2007-04-29
> **mordak13 said:**
> I had success by commenting out the "msdfs proxy = yes/no" in smb.conf. Thanks again for the info. \\:D/

Glad I can help everyone out...except for myself.  I guess I'm SOL.  I've been at this for 2 days.

---

### Post by mordak13 on 2007-04-29
> **jdunn said:**
> Glad I can help everyone out...except for myself.  I guess I'm SOL.  I've been at this for 2 days.
Well I know the feeling I have never had Audacity working and now Amarok is broken too. I have miles to go before I sleep. :wink:

---

### Post by jdunn on 2007-04-29
> **mordak13 said:**
> Well I know the feeling I have never had Audacity working and now Amarok is broken too. I have miles to go before I sleep. :wink:

The above smb.conf file had no lines with "msdfs" yet, you said you commented those lines out.  I used the exact same smb.conf with matching workgroups.  All I did was change the netbios name.  My windows and linux boxes can't see the shares.  So, as far as I can tell, I did nothing different from what you did.

---

### Post by jdunn on 2007-04-29
bump

---

### Post by jdunn on 2007-04-29
bump

---

### Post by MCMcButtah on 2007-04-30
I resolved my server samba issues by first uninstalling samba. I then did a search for samba and deleted any instance of it in the init.d folders. I then re-installed samba. Then after I deleted the mdfs proxy entries in smb.conf samba works great on my server now.

But then there is my workstation. In order to get my kubuntu fiesty workstation to connect I have to comment out all the mounting of the shares in /etc/fstab. Then I reboot. After the boot once I login and am in KDE I uncomment (reactivate) the samba shares in /etc/fstab. Then and only then if I issue a 'sudo mount -a' the samba shares mount fine and everything works until I shutdown. I have to remember to re-comment out the samba shares before I shutdown or I will experience the problem on next boot.

Windows XP connect to the samba shares no problem. As a matter of faxct windows xp running as a guest in vmware under the fiest host can connect with no problem even though the host cannot.

---

### Post by dmizer on 2007-04-30
@jdunn

please post the contents of your smb.conf file.

@MCMcButtah

try mounting your shares with cifs instead of smbfs ... take a look at the second link in my sig.

---

### Post by mrvanes on 2007-05-01
> **MCMcButtah said:**
> After the boot once I login and am in KDE I uncomment (reactivate) the samba shares in /etc/fstab. Then and only then if I issue a 'sudo mount -a' the samba shares mount fine and everything works until I shutdown. I have to remember to re-comment out the samba shares before I shutdown or I will experience the problem on next boot.

Although not a solution, but a far better work-around, you could start making the samba mounts noauto in your fstab. You'd still have to mount them in KDE, but at least you wouldn't have to remember to dis/enable them every boot. I do this all the time, because my laptop may be in an environment where the share is not available, and so it boots without even trying to touch the share, but mounts immediately and transparantly when I use (=click on) it at home.

My smb fstab entry looke like this:

# SMB shares
//kronos/media  /mnt/kronos     smbfs   users,noatime,noauto,guest,username=,password=  0       0


Martin

---

### Post by dmizer on 2007-05-01
@mrvanes

noauto is an fstab option but not a smbfs option.  your smbfs mount is not automatically mounting because it's erroring out, and it's probably causing your desktop to be slow to load.  you'll find kernel errors in your logs.

try this and see if it works better ... comment out your current smbfs fstab line like so:
```
# //kronos/media /mnt/kronos smbfs users,noatime,noauto,guest,username=,password= 0 0
```
and add this line below it:
```
//kronos/media /mnt/kronos cifs guest,rw,file_mode=0777,dir_mode=0777 0 0
```
reboot and you should see much improved performance.

if it causes you problems, simply delete the cifs line and the "#" mark, and you'll be in the same place you were before the change.

---

### Post by mrvanes on 2007-05-02
Hey dmizer!

Thx for your suggestion, but with all due respect I don't think this is true. My laptop boots just fine, there are no boot errors, and if I boot in the neighborhood of kronos it is not mounted after boot. Only after I doubleclick the link to this share on my desktop, mount does it's thing.
I would use cifs instead of smbfs if it were not so picky about user mounts. The line you suggest is wrong in the first place because you forgot to add users, and even if I add that it doesn't let me connect with the share as a mere mortal: 

~$ mount /mnt/kronos/
mount error 1 = Operation not permitted
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

Am I missing something?

---

### Post by dmizer on 2007-05-02
you will not see errors on boot.  you will have to look at the kernel logs.

your fstab line is quite creative so i guessed at it's actual intent.  the "guest" option means that you are mounting a share without password protection ... but you also have the username/password options with blanks.  further, "users" also isn't a valid smbfs option, and frankly i'm quite surprised that the mount works at all.

here are the valid options for samba mount:
> OPTIONS
       [COLOR="Red"]username[/COLOR]=<arg>
              specifies the username to connect as. If this is not given, then
              the  environment  variable   USER  is used. This option can also
              take the form "user%password" or "user/workgroup" or "user/work&#8208;
              group%password" to allow the password and workgroup to be speci&#8208;
              fied as part of the username.

       [COLOR="Red"]password[/COLOR]=<arg>
              specifies the SMB password. If this option is not given then the
              environment  variable  PASSWD  is  used. If it can find no pass&#8208;
              wordsmbmount will prompt for a passeword, unless the  guest  op&#8208;
              tion is given.

              Note that passwords which contain the argument delimiter charac&#8208;
              ter (i.e. a comma &#8217;,&#8217;) will failed to be parsed correctly on the
              command  line.  However, the same password defined in the PASSWD
              environment variable or a credentials file (see below)  will  be
              read correctly.

       [COLOR="Red"]credentials[/COLOR]=<filename>
              specifies  a  file that contains a username and/or password. The
              format of the file is:

              username = <value>
              password = <value>

              This is preferred over having passwords in plaintext in a shared
              file,  such  as  /etc/fstab.  Be sure to protect any credentials
              file properly.

       [COLOR="Red"]krb[/COLOR]    Use kerberos (Active Directory).

       [COLOR="Red"]netbiosname[/COLOR]=<arg>
              sets the source NetBIOS name. It defaults to the local hostname.

       [COLOR="Red"]uid[/COLOR]=<arg>
              sets  the uid that will own all files on the mounted filesystem.
              It may be specified as either a username or a numeric uid.

       [COLOR="Red"]gid[/COLOR]=<arg>
              sets the gid that will own all files on the mounted  filesystem.
              It may be specified as either a groupname or a numeric gid.

       [COLOR="Red"]port[/COLOR]=<arg>
              sets the remote SMB port number. The default is 445, fallback is
              139.

       [COLOR="Red"]fmask[/COLOR]=<arg>
              sets the file mask. This determines the permissions that  remote
              files have in the local filesystem. This is not a umask, but the
              actual permissions for the files. The default is  based  on  the
              current umask.

       [COLOR="Red"]dmask[/COLOR]=<arg>
              Sets  the  directory  mask. This determines the permissions that
              remote directories have in the local filesystem. This is  not  a
              umask,  but  the actual permissions for the directories. The de&#8208;
              fault is based on the current umask.

       [COLOR="Red"]debug[/COLOR]=<arg>
              Sets the debug level. This is useful for tracking down SMB  con&#8208;
              nection  problems.  A suggested value to start with is 4. If set
              too high there will be a lot of output, possibly hiding the use&#8208;
              ful output.

      [COLOR="Red"] ip[/COLOR]=<arg>
              Sets the destination host or IP address.

       [COLOR="Red"]workgroup[/COLOR]=<arg>
              Sets the workgroup on the destination

       [COLOR="Red"]sockopt[/COLOR]=<arg>
              Sets the TCP socket options. See the smb.conf(5)  socket options
              option.

       [COLOR="Red"]scope[/COLOR]=<arg>
              Sets the NetBIOS scope

       [COLOR="Red"]guest[/COLOR]  Don&#8217;t prompt for a password

       [COLOR="Red"]ro[/COLOR]     mount read-only

       [COLOR="Red"]rw[/COLOR]     mount read-write

       [COLOR="Red"]iocharset[/COLOR]=<arg>
              sets the charset used by the Linux side for codepage to  charset
              translations  (NLS).  Argument  should be the name of a charset,
              like iso8859-1. (Note: only kernel 2.4.0 or later)

      [COLOR="Red"] codepage[/COLOR]=<arg>
              sets the codepage the server uses. See the iocharset option. Ex&#8208;
              ample value cp850. (Note: only kernel 2.4.0 or later)

       [COLOR="Red"]ttl[/COLOR]=<arg>
              sets how long a directory listing is cached in milliseconds (al&#8208;
              so affects visibility of file size and date changes).  A  higher
              value means that changes on the server take longer to be noticed
              but it can give better performance on large  directories,  espe&#8208;
              cially over long distances. Default is 1000ms but something like
              10000ms (10 seconds) is probably more reasonable in many  cases.
              (Note: only kernel 2.4.2 or later)
any other option in your fstab line will create an error.

try this line (again, given your previous fstab line it's still a best guess):
```
/kronos/media /mnt/kronos cifs user=UN,password=PW,rw,file_mode=0777,dir_mode=0777 0 0
```
of course ... replacing "UN" and "PW" with the username and password needed to connect to your remote share.

---

### Post by MCMcButtah on 2007-05-02
dmizer thank you very much for your help. I have been trying to mount cifs and have been encountering a permissions issue that does not make sense to me. Check this out...

Here is my original entry in fstab that works when I do a 'sudo mount -a' at the terminal as long as it was done after booting into KDE:

//192.168.0.123/MUSIC /mnt/Music smbfs credentials=/etc/samba/user,rw,uid=berryberry   0   0

Here I tried this entry based on your recommendations:

//192.168.0.123/MUSIC /mnt/Music cifs credentials=/etc/samba/user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

I also tried:

//192.168.0.123/MUSIC /mnt/Music cifs credentials=/etc/samba/user,rw,uid=berryberry   0   0

This happens:

berryberry@shiraz:/etc/samba$ sudo mount -a
mount error 13 = Permission denied


Here is the really bizarre thing though. I tried to mount manually and look what happens. I enter this:

sudo mount -t cifs //192.68.0.123/MUSIC /mnt/Music -o username=mcmcbuttah,password=!27foosb@ll,iocharset=utf8,file_mode=0777,dir_mode=0777

And it says this command is not recognized:

sudo mount -t cifs //192.68.0.123/MUSIC /mnt/Music -o username=mcmcbuttah,password=cd Desktop/foosb@ll,iocharset=utf8,file_mode=0777,dir_mode=0777

See what it did to my password? Weird. If I enter the start to my password which is !27 at a terminal
it does this:

berryberry@shiraz:/etc/samba$ !27
cd Desktop/

Interestingly last time I did it it the response was ifup -a and not cd Desktop/. Is ! a reserved character or something? Can I escape it?  

Thanks again.

---

### Post by dmizer on 2007-05-02
yes, "!" is a command character.  but that doesn't mean you can't use it in your password.  you'll just have to rely on a credentials file.

try this:
```
//192.168.0.123/MUSIC /mnt/Music cifs credentials=/etc/samba/user,rw,uid=berryberry,file_mode=0777,dir_mode=0777 0 0
```

also, you created a credentials file earlier to work with smbfs.  if you created the file with a gui text editor like kate or gedit, you'll need to go back and edit the file with something like nano (a command line text editor).  erase the entire content and re-enter the un/password lines.

---

### Post by Raptor Ramjet on 2007-05-03
Something that has got me slightly further along...

Following lots of searching I found a post at [http://lists.samba.org/archive/samba/2006-August/124073.html]("http://lists.samba.org/archive/samba/2006-August/124073.html")   which mentioned a problem with "passdb backend = tbdsam guest" so I edited my smb.conf file to remove the "guest" at the end of the line.  i.e. that section of my smb.conf now looks like this:

> # If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  

#   passdb backend = tdbsam guest <-- Previous value

   passdb backend = tdbsam


After this I can now use "sudo smbpasswd -a username" and it works.  However I still can't see my shares either from my Windows box or from within Nautilus.

I'll update y'all again if (when ?) I get it working.

---

### Post by Raptor Ramjet on 2007-05-04
Well after rebooting my machine Samba has now started working again so the last smb.conf file change seems to have sorted it.   This is after I'd manually restarted samba and nmbd etc. etc.

How Windows like :)

Still Samba now works again for me so there you go.  Hope the info is of use to someone.

---

### Post by MCMcButtah on 2007-05-04
> **dmizer said:**
> yes, "!" is a command character.  but that doesn't mean you can't use it in your password.  you'll just have to rely on a credentials file.

try this:
```
//192.168.0.123/MUSIC /mnt/Music cifs credentials=/etc/samba/user,rw,uid=berryberry,file_mode=0777,dir_mode=0777 0 0
```

also, you created a credentials file earlier to work with smbfs.  if you created the file with a gui text editor like kate or gedit, you'll need to go back and edit the file with something like nano (a command line text editor).  erase the entire content and re-enter the un/password lines.

cifs is working great for me now. Even if the remote share is off now my desktop does not hang on bootup waiting to connect like smbfs. Perfect. Thanks again for all your help.

---

### Post by mrvanes on 2007-05-08
@dmizer:

Been away for a couple of days.

Thx for your input, but I'll leave it at this. Never fix a working system they say ;)

The 'users' option in my fstab line is really doing it's work. If I remove it, I can't mount kronos as mere mortal. The user= and passwd= options can be removed I know, they were some legacy remainder of earlier testruns with and without passwords and guest account settings untill I got it working with guest access like I wanted.

cifs in no way lets me mount kronos as a simple user, which is not acceptable for me, so it's just no option.

---

