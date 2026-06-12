---
title: "can't login after changing hostname"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by bhavya juneja on 2010-09-20
Hi all,
I changed my computer's name using the command

> gksudo gedit /etc/hostname /etc/hostsand changed old_hostname to new_hostname in both files.

When I rebooted while loading it gave an error "hostname main process(459) terminated with status 1". After then it showed my login page with new computer name but when I enetered my password it shows a blank screeen for a second and returns back to login page. So, I can't login.

Can anyone help in repairing this??

---

### Post by warfacegod on 2010-09-20
I would use the recovery kernel in GRUB, drop to a shell, issue the startx command (careful, you'll be root!) and navigate to those files and set them back the way they were.

---

### Post by bhavya juneja on 2010-09-20
I am so delight someone replied.
> I would use the  recovery kernel in GRUB, drop to a shell, issue the startx command  (careful, you'll be root!) and navigate to those files and set them back  the way they were.
                                                                              But I am not quite familiar with startx command. Can you please tell me exactly what command I have to write?

---

### Post by migs73 on 2010-09-20
startx will just start the GUI allowing you to browse to the files as before.
The command is just

startx

and then press enter.

---

### Post by bhavya juneja on 2010-09-20
Thanks a lot, I corrected those files back to what they were and everything's working fine now.

But now as I have to change my computer's name what I have to do or why it happened? I think it is because the name I wrote had two words with space between them and I wrote them without quotes. Is that so?

---

### Post by warfacegod on 2010-09-20
I'm not sure exactly why it failed.

Ubuntu Tweak has a utility for changing host names that is likely to work properly. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by philinux on 2010-09-20
> **bhavya juneja said:**
> Thanks a lot, I corrected those files back to what they were and everything's working fine now.

But now as I have to change my computer's name what I have to do or why it happened? I think **it is because the name I wrote had two words with space between them and I wrote them without quotes.** Is that so?

[https://bugs.launchpad.net/ubuntu/+source/hostname/+bug/52335](https://bugs.launchpad.net/ubuntu/+source/hostname/+bug/52335)

See post #8.

---

### Post by bhavya juneja on 2010-09-20
Thanks for telling the bug. But now I changed it to a name with no space but an ' included. It still gives that error but has no problem in login after that.
Is there any hidden problem it??

---

