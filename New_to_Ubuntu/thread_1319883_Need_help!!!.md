---
title: "Need help!!!"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by berri67 on 2009-11-08
I have Ubuntu 8.04 +LTS version on a Dell Mini and I have a problem. 

I updated my machine and now I am unable to shut my machine off.  Also the internet comes up and asks for my password, when it automatically had signed on by itself.  

My question is this:  How do I restore to a previous time than when I did the update?  Is there a command to do this?

Thanks for any help.

---

### Post by duanedesign on 2009-11-09
What type of Dell Mini do you have?

When you say it wont shut off, what is happening? Does it do nothing? Does it freeze?

If you open a Terminal (Applications, Accesories > Terminal) and issue the command:

```
/sbin/shutdown -hP now
```

What is the result?

---

### Post by Bucky Ball on 2009-11-09
If you can't get to a terminal because the machine is frozen, try ctl/alt/backspace. That should get you back to the login screen at least.

8.04 LTS has just had a kernel upgrade and if you just updated you are probably running the new kernel. When you reboot, the last kernel you were using should be in the list (third down under the new kernel's recovery option) so just choose that.

Also, try running the recovery boot for the current kernel (second on the list).

---

### Post by berri67 on 2009-11-12
> **Bucky Ball said:**
> If you can't get to a terminal because the machine is frozen, try ctl/alt/backspace. That should get you back to the login screen at least.

8.04 LTS has just had a kernel upgrade and if you just updated you are probably running the new kernel. When you reboot, the last kernel you were using should be in the list (third down under the new kernel's recovery option) so just choose that.

Also, try running the recovery boot for the current kernel (second on the list).

Would you kindly advise how I would get to this new kernel?  Is it in the terminal mode or is there a command to get it?

The machine doesn't turn off, it just doesn't do anything, I have to hold down the button to turn it off myself.

Thanks for any help.

---

### Post by Bucky Ball on 2009-11-14
Second on the grub menu list at boot. Ends in (recovery)

---

