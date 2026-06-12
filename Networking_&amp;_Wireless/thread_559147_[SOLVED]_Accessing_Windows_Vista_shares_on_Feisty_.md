---
title: "[SOLVED] Accessing Windows Vista shares on Feisty via Samba"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2007-09-24
I finally have Samba configured. I can view my Feisty shares from Vista, but not vice versa. When I open up Network from Feisty I see my two machines. I double click my Vista machine and it shows  the shares. I attempt to open a file from a share and I get the following error: Nautilus cannot display "smb://willy-velocity/Public/Pictures". Obviously from attempting to open the Pictures folder in Vista (willy-velocity is my Vista machine). I don't know how to build anything from source, how do I resolve this issue?

---

### Post by dmizer on 2007-09-24
try the second link in my sig.

---

### Post by JawsThemeSwimming428 on 2007-09-25
Is there a way to do it without using cifs?

---

### Post by dmizer on 2007-09-25
yes but, there are some distinct advantages with cifs, not the least of which are:

1) cifs is maintained.
2) cifs is much faster.
3) cifs allows file transfers larger than 2gig.
4) cifs is more stable and reliable.

the only time i would suggest using smbfs instead of cifs is when you have a network device which does not support cifs.  any other time, you should be using cifs.

is there something about cifs which is not meeting your needs?

---

### Post by JawsThemeSwimming428 on 2007-09-25
I am in no way an expert on this subject. The main reason I am not sure if I want to switch is because of the difficulty I had in getting what I have working to work. Right now I am able to view, copy, and edit my Feisty shares from Vista, but not the other way around. Can you tell me some more in depth advantages to using cifs? Also, is there a detailed and somewhat easy to follow guide on how to switch from smbfs to cifs for my setup: 

  - Vista Home Premium networked with a WUSB54GC Linksys wireless adapter
  - Feisty networked with a WUSB54Gv4 Linksys wireless adapter

Thanks for the help.

---

### Post by dmizer on 2007-09-26
configuring ubuntu to allow vista to view its shares has nothing to do with ubuntu being able to see vista shares.

cifs and smbfs = view shares on windows computers from ubuntu.
configuring samba.conf = allowing windows to see shares on ubuntu.

both smbfs and cifs are used for ubuntu to windows connectivity.  cifs simply does the job better in most cases.  but neither effects windows to ubuntu connectivity.

---

### Post by JawsThemeSwimming428 on 2007-09-26
OK if I follow the steps from the second link in your sig. I will be able to switch from smbfs to cifs? Is there anything else I would need to do in order to have cifs and Samba work properly?

---

### Post by JawsThemeSwimming428 on 2007-09-26
dmizer,

 Also, in the Disclaimer in your walkthrough it says that I can not be using OPENDNS. How do I tell if I am using that (sorry I am still learning)? In the future I might want to use a NAS device. Are there any specific models that do work?

---

### Post by itzabo on 2007-09-26
Read this thread.
It worked for me seeing how I wrote it....

[http://tinyurl.com/2rsy25]("http://tinyurl.com/2rsy25")

---

### Post by dmizer on 2007-09-26
> **JawsThemeSwimming428 said:**
> dmizer,

 Also, in the Disclaimer in your walkthrough it says that I can not be using OPENDNS. How do I tell if I am using that (sorry I am still learning)? In the future I might want to use a NAS device. Are there any specific models that do work?

actually, that's not true.  i need to update that with the proper work around.  most likely, if you don't know if you're using opendns or not, you are not.  opendns is something you would have to set up yourself manually.

open dns allows you to use "open" dns servers instead of your internet provider's DNS servers.  [www.opendns.com](www.opendns.com) for more information.

there are many nas devices which work perfectly.  some are listed in the thread if you care to sift through it.  i do not have a nas device, nor do i plan to get one so i can't make any suggestions for you in this area.

following the steps in my howto will allow you to connect to windows vista shares using cifs.  it has nothing to do with smbfs or switching.  if you've already made attempts to connect to your shares using smbfs, my howto will not affect that.

---

### Post by JawsThemeSwimming428 on 2007-09-26
Alright, thanks for your help and information. I will be trying your guide tomorrow night so if possible, check back here tomorrow night and I will let you know how it goes.

---

### Post by JawsThemeSwimming428 on 2007-09-27
OK, I followed your how to word for word  and I was very happy when I was done to see my Vista share sitting on my desktop. I was able to browse and edit it. However, after I rebooted Vista and Feisty, I can no longer access my Feisty shares from Vista. I get the following error message when  trying to open my mapped drive (Feisty share): "An error occurred while reconnecting Z: to \\WUBUNTU\MyFiles. Microsoft Windows Network: The group name could not be found. This connection has not been restored" Then when I try to re-map it I get: "\\WUBUNTU\MyFiles is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.The group name could not be found." Do I need to change something in my smb.conf? I am not sure how to fix this...what should I do?

---

### Post by dmizer on 2007-09-27
that should not happen.  i don't know why it would.  can you post the contents of your smb.conf?

---

### Post by JawsThemeSwimming428 on 2007-09-27
[global]
    ; General server settings
    netbios name = wubuntu
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
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

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

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = willy
    force group = willy

---

### Post by dmizer on 2007-09-27
change this option:
```
wins support = yes
```
to:
```
wins support = no
```
restart samba:
```
sudo /etc/init.d/samba restart
```
and try to reconnect to your share from vista.

if that doesn't work, please post the output of:
```
smbtree
```

---

### Post by JawsThemeSwimming428 on 2007-09-27
I did that, then I restarted Samba and rebooted. When Feisty was shutting down it went to black screen with two error messages (it went away quick so I could not write them down). I think they both started with a bunch of numbers and then said CIFS VFS?

smbtree output:

WORKGROUP
        \\WUBUNTU        
                \\WUBUNTU\IPC$                  IPC Service ()
                \\WUBUNTU\MyFiles        
                \\WUBUNTU\print$         
        \\WILLY-VELOCITY 
                \\WILLY-VELOCITY\Users          
                \\WILLY-VELOCITY\Public         
                \\WILLY-VELOCITY\IPC$                   Remote IPC
                \\WILLY-VELOCITY\C$                     Default share
                \\WILLY-VELOCITY\ADMIN$                 Remote Admin

When I rebooted it did not remount my Vista share on Feisty and I still get an error on Vista for my Feisty share.

---

### Post by dmizer on 2007-09-27
i have a fix posted in my howto for the cifs vfs:
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

okay, try this:
change your fstab line to include the actual ip address of your vista machine instead of "WILLY-VELOCITY"

then do the following command:
```
sudo killall winbind
```

restart samba:
```
sudo /etc/init.d/samba restart
```

and try remounting the share from vista.

---

### Post by dmizer on 2007-09-27
sorry for the double post, but i believe i've found your answer:

[http://ubuntuforums.org/showpost.php?p=2631477&postcount=3](http://ubuntuforums.org/showpost.php?p=2631477&postcount=3)
have you added your vista user account to your ubuntu machine?

---

### Post by JawsThemeSwimming428 on 2007-09-27
I don't know if this matters or not but both of these machines are running on Static IP's (when I installed Samba, in order to use WINS support, you needed to have static instead of DHCP). I think I did add my Vista user in Ubuntu based on the guide I followed by Stormbringer ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)). Is there a way to check just to make sure? Also, as you said I changed the wins support option to no in my smb.conf. What are the benefits of enabling this option and can I? I'm going to do what you posted below as soon as possible (tonight). Thanks for all of your help.

---

### Post by dmizer on 2007-09-28
the samba option "wins support" is used when you want your ubuntu server to act as the netbios wins host.  in this case, you have a windows client in network which will handle the netbios resolution, so it's not necessary to have the option functioning in your smb.conf.  what's more, it's possible that by enabling netbios name resolution to your ubuntu computer created a conflict in netbios resolution, so that's why i suggested that you disable it.  again, since you have a windows computer in your network, it's not necessary to include this option.

it might make things easier if you actually point your smb.conf file to the netbios host by adding the following option:
```
wins server = <ip address of your vista computer>
```

adding "wins" to the option "name resolve order" is what gives you name resolution across the network so your vista computer can see your ubuntu server.

let me know how your testing turns out.  i'll keep my eyes open, i vaguely remember running into this before.

---

### Post by JawsThemeSwimming428 on 2007-09-28
Ok I haven't done the CIFS VFS fix yet because I am a bit confused on the steps after reading through the thread (I posted a question there if you have a chance to look and know the answer). I ran the commands you told me to and added that to fstab and I can access my Vista share from Feisty but  I am still getting an error when I try to map the drive in Vista to my Feisty share. When I am mapping the drive and  I browse to my Feisty machine, it shows my share but when I try to select it I get the following error: 
"An error occurred while reconnecting Z: to \\WUBUNTU\MyFiles. Microsoft Windows Network: The group name could not be found. This connection has not been restored" Then when I try to re-map it I get: "\\WUBUNTU\MyFiles is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.The group name could not be found"

What next?

---

### Post by JawsThemeSwimming428 on 2007-09-28
Also, my Vista share is not mounting automatically on Feisty when I reboot. Any idea?

---

### Post by dmizer on 2007-09-28
okay ... try this:
```
sudo aptitude install avahi-daemon
```

as for not being able to remount on reboot, are you using a usb wireless adaptor, or wireless of some kind?

---

### Post by JawsThemeSwimming428 on 2007-09-28
Yes, I am using a Linksys WUSB54Gv4 USB wireless adapter...is that an issue?

---

### Post by dmizer on 2007-09-28
could be just a matter of timing.  usb gets loaded late in the boot process, so ubuntu may be trying to connect to your share before you have an active connection to the network.

as root (sudo), try adding this line:
```
mount -a
```
to the file: /etc/rc.local

it needs to go before the "exit 0" like so:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount -a
exit 0
```

that should make your shares mount on boot.

---

### Post by JawsThemeSwimming428 on 2007-09-28
I tried running sudo aptitude install avahi-daemon and I didn't get any errors. However, I am still unable to access my Feisty shares from Vista. I am still getting the same error message when I try to map or access it. What next?

---

### Post by JawsThemeSwimming428 on 2007-09-28
Also, thank you, my Vista share now loads on Feisty at boot.

---

### Post by dmizer on 2007-09-28
> **JawsThemeSwimming428 said:**
> I tried running sudo aptitude install avahi-daemon and I didn't get any errors. However, I am still unable to access my Feisty shares from Vista. I am still getting the same error message when I try to map or access it. What next?

let's test something.

in your smb.conf file, change these two options:
```
security = user
guest ok = no
```
to this:
```
security = share
guest ok = yes
```
save and restart samba:
```
sudo /etc/init.d/samba restart
```
then see if you can access your share using the network browsing tool.

glad to see your ubuntu is working properly now, sorry about the pain with vista.

---

### Post by JawsThemeSwimming428 on 2007-09-29
Thanks! I edited smb.conf to reflect those changes but still no luck. What could it be? I did not change anything in my smb.conf or anything to do with my Feisty shares or Vista permissions.

---

### Post by dmizer on 2007-09-29
i'm not sure what the deal is here.  that should allow access to anyone.

lets try readding your ubuntu user to the samba group by the following commands:
```
sudo smbpasswd -L -a willy
sudo smbpasswd -L -e willy
```
restart samba:
```
sudo /etc/init.d/samba restart
```

and try again.

---

### Post by JawsThemeSwimming428 on 2007-09-29
Did what you said and still the same error message on Vista. How could setting this up have affected my Feisty share? It is talking about permissions...I can't think of anything that was changed.

---

### Post by dmizer on 2007-09-29
okay, do you have a firewall installed on either vista or ubuntu?  that's the only other thing i can think of.

if not, i'm going to go chat with the samba folks.

edit:
let's try one more thing.

uninstall winbind via synaptic package manager or:
```
sudo aptitude remove winbind
```

then edit nsswitch.conf and remove the "wins" section.

as root (sudo), edit /etc/hosts, and add a line to the top of the file like so:
vista.ip.address WILLY-VELOCITY

here's an example (in red) from my own hosts file (tokkyu is the name of my windows computer on the network):
```
127.0.0.1 localhost
127.0.1.1 shikoku
[COLOR="Red"]192.168.0.16 tokkyu[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

reboot the computer and see if vista can see ubuntu.

---

### Post by JawsThemeSwimming428 on 2007-09-30
After I added it to the hosts file it connected right up. Right now Vista can see my Feisty share and I  can edit it and vice versa. I tried rebooting both machines again just  to be sure it definitely worked and it does. (I do have firewalls running but I had previously created policies to allow each machine to connect.) Thank you very much I really appreciate all of your help!

---

### Post by dmizer on 2007-09-30
wow ... that was painful.  sorry.  lol ... glad to see we found  a solution for you though.

---

### Post by pxc on 2008-03-02
> **dmizer said:**
> 
let's try one more thing.

uninstall winbind via synaptic package manager or:
```
sudo aptitude remove winbind
```then edit nsswitch.conf and remove the "wins" section.

as root (sudo), edit /etc/hosts, and add a line to the top of the file like so:
vista.ip.address WILLY-VELOCITY

here's an example (in red) from my own hosts file (tokkyu is the name of my windows computer on the network):
```
127.0.0.1 localhost
127.0.1.1 shikoku
[COLOR=Red]192.168.0.16 tokkyu[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```reboot the computer and see if vista can see ubuntu.


Hey. I was dealing with a similar problem on my own machine, and found that your solution solved my problem as well. However, my computers all get IP address by dhcp, so I'd rather not lose winbind. I poked around with some of the settings in nsswitch.conf and found that I was able to fix my Samba shares _and_ still have NetBIOS name resolution. :-D

Here are the relevant lines of /etc/nsswitch.conf
```
passwd:         compat winbind
group:          compat winbind
```I'm not entirely sure, but on some systems, it may also be necessary to modify the "shadow" line.
```
shadow:         compat winbind
```

---

### Post by JawsThemeSwimming428 on 2008-03-04
Thanks. Glad to see you got yours working quicker and less painfully than mine!!!

---

