---
title: "problem: samba mounting win share"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Sudan on 2008-07-06
Hi,
Very newbie here.  I'm trying to setup sharing between Ubuntu machine and Win XP SP2 machine (not a 64 bit machine).

I used this Ubuntu documentation guide [ComprehensiveSambaGuide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide").

I successfully followed instructions down this page up to the guide section entitled: Testing Your Shares.  That includes having followed all the guide's instructions for the window machine.

Per this point in the guide I entered this terminal command and got this response:

kelvin@NeoV:~$ sudo mount -t smbfs -o username=ubuntu,password=ecurb,workgroup=Workgroup,gid=smb,uid=$USER,fmask=770,dmask=770,rw //Sudan/ConSudan4Ubuntu /media/winshares
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
mount error: could not find target server. TCP name Sudan/ConSudan4Ubuntu not found
No ip address specified and hostname not found
kelvin@NeoV:~$ 

I don't understand the warning about fmask and dmask arguments being deprecated.  And to me 770 is an octal value so I'm confused about that.  I did susbstitute file_mode for fmask and dir_mode for dmask in the command string characters but still got the same error.

Not sure if the reason it can't find a hostname is due to the warning about fmask and dmask.  Of if the hostname is another issue.  

I've made sure that the case of the windows workgroup and username and computer name and share name are spelled and capitalized as they are in Windows.  On the windows machine I didn't install any kind of program called samba.  I don't think that there is such an animal for windows.  On the windows machine I just when through all the steps outlined in the beginning of the guide for creating a user and group and the share.

I'm not really sure where to go from here.  Help is appreciated.

---

