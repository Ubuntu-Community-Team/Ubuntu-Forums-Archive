---
title: "Garbled display after recovering from hibernate"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by sdcmunich on 2009-09-05
I have been trying out Hibernate, and it didn't work that well.

Every time I restart, I end up with a garbled screen after GRUB, so I can't log on using X. Booting in text mode using the GRUB recovery option works.

I assume that my hibernate file has a problem, and I would like to delete it / ignore it, so that I can start from a clean boot. Where is that file located?

Or can anyone explain me any other way not to restart from the hibernate file?

Thanks for your help!
/sdc

---

### Post by sdcmunich on 2009-09-06
sorry to bump...

Where can I find info about the hibernate process, where the hibernate file is located, and how I can restart without hibernate?

Thanks for your help,

/sdc

---

### Post by perce on 2009-09-06
This might be completely pointless, but give it a try: I had a similar problem about one year ago, and to fix it I switch to text console bt Ctrl-Alt-f1 and then back to graphic mode by Ctrl-Alt-f7.

In any case, this seems a graphic card issue, and to help people help you, you should tell what card and what driver you're using. You can find this information by the commands 
```
lspci
``` and ```
lsmod
```.

---

### Post by sdcmunich on 2009-09-06
Thanks perce,

Now that you write about graphic card - I actually installed ATI Control Centre a few days ago, and I think this is my first reboot since then.
My graphics card is a Radeon 9600 (not M - the old one).

Ctrl+Alt+F1 doesn't help, this is one of the first things I tried.

Maybe I should try uninstalling the ATI control centre. I will go and look for the apt package name - anyone knows it?

/sdc

---

### Post by sdcmunich on 2009-09-06
Catalyst was the problem indeed, not hibernate.

I found all the Catalyst bits in aptitude and uninstalled them, everything is now working again.

Thanks perce for your help!
/sdc

---

