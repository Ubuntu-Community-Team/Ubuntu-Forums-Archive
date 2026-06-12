---
title: "Having a problem with running CDs"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Phyon on 2009-07-10
So I installed ubuntu about a month ago been struggling threw diffrent problems first time posting about a problem. Well my problem is this I did something a few weeks ago and now I can't run any thing from cds I tried installing World of warcraft wrath of the lich king and found the problem it says under the emblems the picture I am seeing next to the icon is no read when I try and run the installer it goes to wine and tells me access is denied but that is not the only cd I can't run any of my cds now they all tell me the same thing. 
I  am not sure what I did to break it but would love some help if any one knows what I did.


Ok, Slight update after messing with it awhile longer I tried doing the command in the terminal "Wine installer.exe" with the installer I was in the directory and I got this error message don't know if it helps continuing to mess with it see if I come up with something else that could help some one help me.  I been trying a few things and one command let me see more files on the cd then just the two it currently shows which right now it shows directX and Instaler when I used it showed the other stuff on the cd.

application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

---

### Post by Phyon on 2009-07-10
So this is a bump and another update I been looking into my problem and I think it may have something to do with fstab. I was able to edit it and put rw before /media/cdrom0  but that seemed to do nothing so I got rid of it but here is my fstab file contents if some one sees something that should be different. 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=fec1e151-3cd6-42d1-a1c8-86d5a49380a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=4f99466c-ae10-4e90-a89a-bc78e152d2ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Phyon on 2009-07-10
can probabbly delete this post I decided to go back to windows tried figuring this out and kinda not getting any where and honestly it has been going threw one problem after another but I think this one has done it for me backing up all my stuff and going to windows.

---

### Post by LewRockwell on 2009-07-10
Is that one of those new custom netbooks?

You might have better luck with Ubuntu 9.04 Jaunty Jackalope LiveCD Installer while using those external optical drives

.

---

### Post by IHeequ5i on 2009-07-10
Sorry to see you go.

But I wish you'd given this forum more than 13 hours to help you out.

---

### Post by Phyon on 2009-07-10
It was not the forum I actually got partial help in another place and it was exhausting work to try and fix it and it came out to do nothing my only suggestion was to pretty much format they wanted me to to hackintosh but blah I say to that.  I actually recently updated to 9.04 and honestly the cds worked just fine I found the problem came about because I mounted a iso wrong and it was the cause of the problem but the solutions I went threw did not work out. I like ubuntu but it seems like far to much hassel for what you get.

---

