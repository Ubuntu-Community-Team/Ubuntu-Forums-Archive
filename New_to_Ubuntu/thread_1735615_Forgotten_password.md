---
title: "Forgotten password?"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by KellyNicole on 2011-04-21
Hello everyone,
My name is Kelly and I'm 15.

I've got myself in a little bit of a predicament. 
I have my computer password-ed, simply because the people I live with tend to be nosy. 
Yesterday I went back and changed passwords on a couple of accounts, (Facebook, g-mail, etc.) I changed my login password for Ubuntu and guess what?
I FORGOT IT!!!!
I was wondering if there was some way to fix this, other than reinstalling Ubuntu on my computer and losing everything I had on it. 
I'm new to Ubuntu, as you can probably tell, so if anyone could explain concisely how to fix this, I'd appreciate it. :(

---

### Post by mikewhatever on 2011-04-21
You can reset the password using this -> [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword).

---

### Post by mathgeek2000 on 2011-04-21
> **mikewhatever said:**
> You can reset the password using this -> [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword).

Overview of steps:
  1. From the Grub or Grub2 menu select the 'Recovery Mode'
      -> Select 'Root' from the menu listed.
    --> This leaves you in single user mode, logged in as 'root.
      -> Be careful from here, as you have 'super duper access'

Question: Did you encrypt your home directory when you set up your system?
    change dir to /home/<username>
     ```
#cd /home/<username>
#ls
```
    
If you see Documents, Desktop, Downloads etc you're good. If not when you change the password, as below, it will not properly decrypt your directory. -- see next post on that. 

  3. from the '#' prompt type:
         ```
#passwd <username>
```
            -> Enter a new password.
            -> Re-enter password.
  4. Type exit
  5. From the menu continue normal boot.
  6. You will get a login prompt.
  7. login as yourself, with your new password.
       ```
login: <username>
```

---

### Post by mathgeek2000 on 2011-04-21
Notes: If you don't have a Grub2 menu on Boot, holding the Shift key on Boot will display it. 'Esc' for Grub legacy. --> This is easiest.

Only if you are having trouble getting to the grub menu: -> This is tricky: from a LiveCD, or Parted Magic CD: Boot from LiveCD, mount the partion with /boot' ex: sda1: /boot' sda2: '/' or sda1: '/' sda2: swap

 -> in either case: find /boot/grub/grub.cfg & edit it: -> Yes this is why I say tricky.

Near the top there should be a line 'set default="0"

```
...
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
...
```

Count the lines starting "menuentry ' <Text Description>' { "
Starting with 0 as the first, count to the one which includes '(recovery mode)' in the description.
  --> Usually this will be '1', i.e. normal: '0' recovery mode '1' (the second one)

Back in the set default line, change "0" to "1" 
Save and reboot, you should boot into recovery mode, by default.

When done, and all set, be sure to run:
  'update-grub' to fix the grub.cfg menu.

---

