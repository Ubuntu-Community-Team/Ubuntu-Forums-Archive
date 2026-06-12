---
title: "What Is It?"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Rajcyberfox on 2010-11-24
Thanks, i burnd the disc usinh ImgBurn.And Installed it with duelboot Vista star,
when i boot the computr it prompts me to the several booting option of ubuntu.
Says..
1.ubuntu generic
2.ubuntu generic(safe mood)
3.memory test(memtest sda1)
4.memory test() 
etc what is it?? At the 
5.window vista loder, which was my past o.s.

And sir my macromax modem is not working.i configured it as mobile connector as default but dont know from where i should connect it??

And one last Question Sir,Ubuntu provides us a terminal,then where is Shell?where is bash shell & Cshell??and how can i open it???thank you!

---

### Post by yankysunny on 2010-11-24
This is a GRUB bootloader which display your boot menu.

Ubuntu generic is default boot option and ubuntu generic(safe mode) is used when u want the terminal access while doing some repairing.

In terminla, it gives u bash as default shell. You can use ksh, csh and other shells just by typing them in terminal

---

### Post by Rajcyberfox on 2010-11-24
> **yankysunny said:**
> This is a GRUB bootloader which display your boot menu.

Ubuntu generic is default boot option and ubuntu generic(safe mode) is used when u want the terminal access while doing some repairing.

In terminla, it gives u bash as default shell. You can use ksh, csh and other shells just by typing them in terminal

 thanks,so is there any  diffrents between that shell??

And what repairing is done in safe mode??

---

### Post by yankysunny on 2010-11-24
There is no big difference in the shells that you are forced to use that particular shell. try to google it if you are really interested in bits and pieces of the differences. They are very specific and usually u dont observer them until you are going to do some specific task.

When u boot in safe mode, u get the terminal .login into that and if you did some wrong editing in config files or want to run some debugging, u can use that

---

### Post by upshutdown on 2010-11-24
> **Rajcyberfox said:**
> thanks,so is there any  diffrents between that shell??

And what repairing is done in safe mode??

As to which shell to use, I really recommend sticking to bash if you are just starting out. It is the most commonly used shell, and will be the easiest to use when looking for help and what not... (at least when starting out)

and repairing? Safe mode is simply the way the operating system loads when there is some form of a system critical "problem" occurring. It basically restricts certain configuration/system files from being executed, stops certain drivers from being loaded including maybe graphics...stuff like that

So when you ask what repairing is done, do you have a specific problem? You're distribution could very well do some common error checking and what not, but more likely then not any problem you have will be dealt with manually.

---

### Post by Rajcyberfox on 2010-11-24
> **yankysunny said:**
> This is a GRUB bootloader which display your boot menu.

Ubuntu generic is default boot option and ubuntu generic(safe mode) is used when u want the terminal access while doing some repairing.

In terminla, it gives u bash as default shell. You can use ksh, csh and other shells just by typing them in terminal

> **upshutdown said:**
> As to which shell to use, I really recommend sticking to bash if you are just starting out. It is the most commonly used shell, and will be the easiest to use when looking for help and what not... (at least when starting out)

and repairing? Safe mode is simply the way the operating system loads when there is some form of a system critical "problem" occurring. It basically restricts certain configuration/system files from being executed, stops certain drivers from being loaded including maybe graphics...stuff like that

So when you ask what repairing is done, do you have a specific problem? You're distribution could very well do some common error checking and what not, but more likely then not any problem you have will be dealt with manually.

thanks,lets me check and go deeper in it..thank

---

