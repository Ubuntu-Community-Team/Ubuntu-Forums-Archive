---
title: "Dual booting Mint 7 with Ubuntu, Grub problem"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by JoePublic9 on 2009-10-30
I wanted to try out Linux Mint 7 so I partitioned my HD and installed it.
All went well but now when I boot I get the Mint grub. It gives me the Ubuntu option and I even changed the default to 4 so that Ubuntu is default but I want to boot straight to Ubuntu, Unless, I hit ESC and choose Mint.
  I assume that Mint hijacked my grub and that I can get back to the Ubuntu grub but after various searches I can't seem to find the solution.
  Anybody?
 Thanks in advance for you help.
             Joe

P.S. Sorry if this is not a good post. Had a late night and am very hungover.

---

### Post by ranch hand on 2009-10-30
Assuming that you have Jaunty, boot from your Live CD and;
```

sudo grub
[code]
You will then get a grub prompt "grub>".  The following commands go after the grub prompts;
[code]
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```
Where x is the drive number listed after the "find" command and y the partition number.

You will then need to;
```

gksudo gedit /boot/grub/menu.lst

``` 
and add an entry for Mint.  You should be able to just go to that file in Mint from your Home menu in Ubuntu and copy/ paste to the menu.lst in Ubuntu.

Save the file and reboot and all should show up on your menu on the screen.

---

### Post by JoePublic9 on 2009-10-31
Thank you Sir!
  That worked perfectly. I love Ubuntu and it's community.
 Thanks again.
        Joe

---

