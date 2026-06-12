---
title: "At my wits end accessing shares on Vista"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by iammike on 2007-05-20
I won't bother going in to all the problems browsing to a Vista box since those are well documented problems in Samba.

I will say that after initial problems with that, I learned that if I installed smbfs and used smbmount I could mount the shares with no problems.  I even added the mounts to my /etc/fstab and it worked perfect for a couple of weeks.

Today I changed the network IP range that my network runs on and since then I've had nothing but problems but I can't see how doing this would have caused so many problems.

What I mean by the above is that, for example, my IP range used to be 199.199.199.100-200 but I changed it to 10.10.10.200-202 and then restarted my computers so they obtained new IP's by way of DHCP and ran all programs from a clean boot.

Everything works fine except I noticed that my fstab mounts were no longer working even though the IP specified in the fstab entry is correct for my Vista machine.

I went to the command line and ran a sudo mount -a and bam, they were there.  I tried to figure out why they were not mounting on boot but never got anywhere and couldn't find any errors in /var/log/messages or /var/log/samba/log.smbmount.

So since then, everytime I boot the system I have to open a terminal and run sudo mount -a and although I know I shouldn't have to, I can live with that for now since I rarely ever have to restart for anything.

Now, the problem that has pretty much got me at the end of my rope.....

Once I do the mount -a and everything looks fine, after a period of time the mounts will suddenly stop working.  They don't unmount but if I try to access the directory in either the terminal or browser....it just sits there for a looooooong time.

Only clues I have are some errors like this in the /var/log/messages:

```
May 20 00:41:45 iammike-desktop2 kernel: [ 8191.775379] SMB connection re-established (-5)
May 20 00:41:46 iammike-desktop2 kernel: [ 8193.437582] SMB connection re-established (-5)
May 20 00:41:48 iammike-desktop2 kernel: [ 8195.126946] smb_proc_readdir_long: error=-13, breaking
May 20 01:06:27 iammike-desktop2 -- MARK --
May 20 01:13:37 iammike-desktop2 kernel: [10102.839231] smb_add_request: request [e490bee0, mid=60850] timed out!
May 20 01:14:07 iammike-desktop2 kernel: [10132.811523] smb_add_request: request [e490bee0, mid=60851] timed out!
May 20 01:14:07 iammike-desktop2 kernel: [10132.811538] smb_lookup: find //Anime failed, error=-5
May 20 01:14:37 iammike-desktop2 kernel: [10162.812317] smb_add_request: request [e490bee0, mid=60852] timed out!
May 20 01:15:07 iammike-desktop2 kernel: [10192.925089] smb_add_request: request [e490bee0, mid=60853] timed out!
May 20 01:15:07 iammike-desktop2 kernel: [10192.925104] smb_lookup: find //Anime failed, error=-5
May 20 01:15:45 iammike-desktop2 kernel: [10230.798663] smb_add_request: request [eab30e60, mid=60854] timed out!
May 20 01:15:45 iammike-desktop2 kernel: [10230.798678] smb_lookup: find //Anime failed, error=-5
May 20 01:16:15 iammike-desktop2 kernel: [10260.771574] smb_add_request: request [eab30e60, mid=60855] timed out!
May 20 01:16:15 iammike-desktop2 kernel: [10260.771589] smb_lookup: find //Anime failed, error=-5
May 20 01:16:45 iammike-desktop2 kernel: [10290.744302] smb_add_request: request [eab30e60, mid=60856] timed out!
May 20 01:16:45 iammike-desktop2 kernel: [10290.744317] smb_lookup: find //Anime failed, error=-5
May 20 01:17:15 iammike-desktop2 kernel: [10320.717127] smb_add_request: request [eab30e60, mid=60857] timed out!
May 20 01:17:15 iammike-desktop2 kernel: [10320.717141] smb_lookup: find //Anime failed, error=-5
May 20 01:17:45 iammike-desktop2 kernel: [10350.689942] smb_add_request: request [eab30e60, mid=60858] timed out!
May 20 01:17:45 iammike-desktop2 kernel: [10350.689956] smb_lookup: find //Anime failed, error=-5
May 20 01:18:15 iammike-desktop2 kernel: [10380.666757] smb_add_request: request [eab30e60, mid=60859] timed out!
May 20 01:18:15 iammike-desktop2 kernel: [10380.666771] smb_lookup: find //Anime failed, error=-5
May 20 01:18:45 iammike-desktop2 kernel: [10410.655563] smb_add_request: request [eab30e60, mid=60860] timed out!
May 20 01:18:45 iammike-desktop2 kernel: [10410.655577] smb_lookup: find //Anime failed, error=-5
May 20 01:19:15 iammike-desktop2 kernel: [10440.628384] smb_add_request: request [eab30e60, mid=60861] timed out!
May 20 01:19:15 iammike-desktop2 kernel: [10440.628398] smb_lookup: find //Anime failed, error=-5
May 20 01:19:45 iammike-desktop2 kernel: [10470.601286] smb_add_request: request [eab30e60, mid=60862] timed out!
May 20 01:19:45 iammike-desktop2 kernel: [10470.601301] smb_lookup: find //Anime failed, error=-5
May 20 01:20:15 iammike-desktop2 kernel: [10500.574109] smb_add_request: request [eab30e60, mid=60863] timed out!
May 20 01:20:15 iammike-desktop2 kernel: [10500.574123] smb_lookup: find //Anime failed, error=-5
May 20 01:20:31 iammike-desktop2 kernel: [10516.791680] smb_lookup: find //Anime failed, error=-512
May 20 01:21:02 iammike-desktop2 kernel: [10547.187800] smb_add_request: request [eab30e60, mid=60865] timed out!
May 20 01:21:30 iammike-desktop2 kernel: [10575.118424] smb_add_request: request [eab30060, mid=60868] timed out!
May 20 01:21:32 iammike-desktop2 kernel: [10577.164567] smb_add_request: request [eab30e60, mid=60869] timed out!
May 20 01:21:32 iammike-desktop2 kernel: [10577.164581] smb_lookup: find //.Trash-iammike failed, error=-5
May 20 01:21:35 iammike-desktop2 kernel: [10577.189374] SMB connection re-established (-5)
May 20 01:22:02 iammike-desktop2 kernel: [10607.141385] smb_add_request: request [eab30e60, mid=60870] timed out!

```

Now a strange thing I see there is that Anime is a folder and if I were to try to go to it directly it would be //computerip/500GB/Anime and not just //Anime but I'm not sure if that is a problem or just how SAMBA works.

If I unmount and remount....it works fine for a bit again then fails out again.  Seems to be no rhyme or reason that I can figure out and I'm just out of ideas.

Here are the entries in my fstab with IP's removed.

```

//computerip/200GBPart2 /home/iammike/vistamount/200gb  smbfs   credentials=/home/iammike/.smbpasswd,uid=1000,gid=1000  0       0
//computerip/500GB      /home/iammike/vistamount/500gb  smbfs   credentials=/home/iammike/.smbpasswd,uid=1000,gid=1000  0       0

```

---

### Post by commbot on 2007-05-20
as for your samba issues, for sure it is related to changing the network numbering. samba is trying to mount the specified folders but can't find them on the network. check your smb.conf file to see if it specifies the network range in there.

man smbmount has this to say

       One  smbfs bug is important enough to mention here, even if it is a bit
       misplaced:

       &#8226;
          Mounts sometimes stop working. This is usually  caused  by  smbmount
          terminating. Since smbfs needs smbmount to reconnect when the server
          disconnects, the mount will eventually go dead. An umount/mount nor&#8208;
          mally fixes this. At least 2 ways to trigger this bug are known.

maybe you've found a third...


good luck

---

### Post by iammike on 2007-05-20
No entries like that in my smb.conf file.

Now this is strange and I'll test over a longer term to see if this maintains stability but I still can't figure out why this would suddenly not be stable in my fstab but be stable this way.

I made a script that uses a sudo smbmount in it to mount with on my laptop since my laptop isn't always on the home network.  I used this script late last night to do some work from another room and the mounts never dropped.

Before I went to bed I copied the script over to the desktop and made the appropriate adjustments to it and mounted the Vista shares that way.  I woke up and they were still mounted.

Weird if you ask me.  lol

---

### Post by weedenbc on 2007-05-22
I was having a similar problem.  I am mapping 4 XP shares and put the appropriate smbmount commands in fstab.  THe problem is that it doesn't always work - sometimes after a reboot it mounts all 4, sometimes only 1, sometimes none.  If I manually run the script they mount just fine.

I think it might be related to the wireless card - it takes the system a bit to sync and connect to my wi-fi network on reboot and I think that delay might be giving fstab problems.

Is there a way to delay the mounting until after the connection is made or maybe I should just run it as a separate script?

---

### Post by dooohkooo on 2007-05-23
I've the same problem.
My configuration is Feisty, no wireless card, and connecting to my NAS with smbfs. This connexion is very unstable and I got the same type of errors in /var/log/syslog.

For information, when I used nautilus sharing system (smb://...), I never had a problem.

Any idea ?

Thx ! :)

---

