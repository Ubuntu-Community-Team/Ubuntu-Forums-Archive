---
title: "Al"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by allanw on 2010-02-12
I downloaded some new ubuntu downloads when asked by the pc.   When directed to restart the pc so the downloads could take effect I received the following message:
GNU GRUB VERSION 1.97 beta4
[ Minimmal Bash - Like line editing is supported for TAB first word.   TAB  list possible command completions anywhere ease tab list possible/file completions ]
SH:GRUB>
I cannot go past this message and cannot access the Ubuntu home page.   I tried startx but it says that that command is not valid.
Anyones help  would be much appreciated.
Allanw

---

### Post by Satoru-san on 2010-02-12
does it let you type :
```
dmesg
```

??

EDIT: probably not. If it does though that could tell us a great deal, are you sure that it didn't say kernel panic or something?

---

### Post by Cheezespread on 2010-02-12
I belive you can list the mounted drives from there. Any idea which is your linux parition ?

```
ls
```

Have a look [here]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot") if you are ok with command line . Helped me a lot when I had grub issues.Have a look under this title--
_Boot a Specific Kernel Manually_

---

### Post by wojox on 2010-02-12
Type this at the "sh: grub> " prompt:

```

search -f --set /vmlinuz
probe  -u --set=UUID $root
linux /vmlinuz root=UUID=$UUID ro
initrd /initrd.img
boot

```

---

### Post by allanw on 2010-02-13
> **Cheezespread said:**
> I belive you can list the mounted drives from there. Any idea which is your linux parition ?
 
```
ls
```
 
Have a look [here]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot") if you are ok with command line . Helped me a lot when I had grub issues.Have a look under this title--
_Boot a Specific Kernel Manually_
 
Please forgive my ignorance of the above commands.   I inserted the command ls and got the answer of 
 
[ loop 0]  [hd 0]   [hd 0,3]  [hd 0,2]  [hd 0,1]
 
if that tells you anything.   I did look in 'here'  but couldn't find the title you listed above.   i did find one similar but not the same.   Still couldn't understand it though.   Hope you can be fof further help.
 
Thanking You
Allan Wehlow

---

### Post by allanw on 2010-02-13
> **wojox said:**
> Type this at the "sh: grub> " prompt:
 
```

search -f --set /vmlinuz
probe  -u --set=UUID $root
linux /vmlinuz root=UUID=$UUID ro
initrd /initrd.img
boot

```
 
Absolute beginner with command lines.   Is the code above all one line and if not how do you get it to format the way you have done it above.   If I press enter to go to the next line I just go back to the SH command.
 
When I did insert the above commands I received the answer   error; no such device/vmlinuz
 
Hope this is of some help.
 
Thanking You
Allan Wehlow

---

### Post by allanw on 2010-02-13
> **Satoru-san said:**
> does it let you type :
```
dmesg
```
 
??
 
EDIT: probably not. If it does though that could tell us a great deal, are you sure that it didn't say kernel panic or something?
 
Typing dmseg just gives error unknown command.   No it didnt say kernel panic or anything else except what I originally quoted.   Any other help would be appreciated.
 
Allan Wehlow;)

---

