---
title: "infuriating screen res"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by reivan on 2008-12-09
hi again ,thanks for responses, but i still cannot figure out how to increase my screen resolution. max choice is 960x600 16:10. apparantly the thing called xorg.conf accepts no editing. the instructions say any changes will be ignored. i understand there was a tool called screens and graphics that was used for this but has been removed. is there something to replace its function? my comp has onboard video called SiS 661x, and i'm using an old trinitron 19" crt (dell logo). thanks for any help.

---

### Post by Tatty on 2008-12-09
If you are using Intrepid then you may be in for a struggle on this.  Most manual configuration of Xorg has been replaced with much improved autoconfiguration.

The Screens and Graphics tool no longer works with the intrepid Xorg and consequently has been removed from the repos.

I am not sure what the best procedure is for when autodetection fails, but AFAIK manual editing of your xorg.conf file should still work.

To edit your xorg.conf file do the following:

1. Back up your current xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
2. load the file for editing with super user powers:
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by prshah on 2008-12-09
> **reivan said:**
> 
 still cannot figure out how to increase my screen resolution. max choice is 960x600 16:10. apparantly the thing called xorg.conf accepts no editing. the instructions say any changes will be ignored. i understand there was a tool called screens and graphics that was used for this but has been removed. is there something to replace its function?

Yes "Screens and Graphics" has been dropped. You can reinstall using this thread [Bring Back Screens and graphics Please!]("http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk") but this is not the recommended method (Though it currently seems to work).

You can manually edit the xorg.conf file; the reconfigure command no longer support graphics resolutions. If you want to know what edits to make, post your /etc/X11/xorg.conf file as well as the resolution you want, and if you can include your refresh rate, it will be helpful.

Instead of all these, you should use xrandr to (dynamically) resize your screen. xrandr is a commandline tool, unfortunately... open a terminal and try```
sudo xrandr --fb 1024x600
``` (Replace 1024x600 with the resolution you want). 

Note: There is a (small) chance that your monitor can be damaged by using incorrect resolutions. So you do this at your own risk.

Also, are you sure the SiS 661x graphics adapter has enough memory to enable the mode you want? Or does it use system memory dynamically?

If the above steps don't work or / and you need more detailed steps, post back. Please also include the following information```
xrandr --verbose
lspci | grep -i graphics
cat /var/log/Xorg.0.log | grep -i graphics
cat /etc/X11/xorg.conf

```

---

