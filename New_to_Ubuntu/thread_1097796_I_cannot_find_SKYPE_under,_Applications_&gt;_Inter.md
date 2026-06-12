---
title: "I cannot find SKYPE under, Applications &gt; Internet"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by L Campbell on 2009-03-16
I'm running 8.04 on a PC and I cannot find SKYPE under, Applications > Internet.

Synaptic tells me I have version 2.0.0.72 - Omedibunt

I tried 'REinstall', then rebooted but it still does not show up.

Skype was working fine in December and the Skype website still shows me with an active account.

If you have a suggestion here, I would appreciate it.

TIA

---

### Post by taurus on 2009-03-16
Have you tried to run it from a terminal to see if it is really on your machine?

```
skype
```
Then, you can add it to your Applications -> Internet in System -> Preferences -> Main Menu.

---

### Post by Berserker v7 on 2009-03-16
Try typing 'skype' in a terminal... maybe that the menu link is broken or something...

---

### Post by L Campbell on 2009-03-16
> **taurus said:**
> Have you tried to run it from a terminal to see if it is really on your machine?

```
skype
```
Then, you can add it to your Applications -> Internet in System -> Preferences -> Main Menu.

Thanks for the suggestion but, unfortunately, it gives me this:-

bash: skype: command not found

Kind regards.

---

### Post by LowSky on 2009-03-16
how did you install skype? I could be that you installed or updated to a version that does not have a menu icon.. it happens

Best option is to use the skype file from the medibutnu repos
these are built for ubuntu users and are perfectly fine to use

follow th instructions to add these repos 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by L Campbell on 2009-03-16
> **LowSky said:**
> how did you install skype? I could be that you installed or updated to a version that does not have a menu icon.. it happens

Best option is to use the skype file from the medibutnu repos
these are built for ubuntu users and are perfectly fine to use

follow th instructions to add these repos 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Thanks, I installed the code for 8.04 and also the code for 'GPG Key'.

I rebooted, then went to Synaptic, where it shows that I still have 2.0.0.72 - Omedibunt and it still doesn't show up in Applications > Internet.

Kind regards.

---

### Post by taurus on 2009-03-16
> **L Campbell said:**
> Thanks, I installed the code for 8.04 and also the code for 'GPG Key'.

I rebooted, **then went to Synaptic, where it shows that I still have 2.0.0.72** - Omedibunt and it still doesn't show up in Applications > Internet.

Kind regards.

But did you install it?  Show a screenshot of synaptic.

---

### Post by L Campbell on 2009-03-16
> **taurus said:**
> But did you install it?  Show a screenshot of synaptic.

I hope this comes through clearly.

Thanks.

---

### Post by taurus on 2009-03-16
How about installing skype also?

---

### Post by L Campbell on 2009-03-16
> **taurus said:**
> How about installing skype also?

Oops!!  You've confused me here.

I thought that the screenshot I sent indicated that SKYPE was installed.

Kind regards.

---

### Post by taurus on 2009-03-16
You have only installed skype-common, not skype itself.  Do you see the square box on the left that is not blue?  No blue, not installed.

So click skype and install it.

---

### Post by Berserker v7 on 2009-03-16
You have to install the 'skype' package... you have only installed the skype-common package now... both are required if you want to use skype...

---

### Post by Pastor_JW on 2009-03-16
> **L Campbell said:**
> Oops!!  You've confused me here.

I thought that the screenshot I sent indicated that SKYPE was installed.

Kind regards.

You also still need Skype, the one right above the common files normally is what is best for most installs.  If you would have clicked on Skype it would have automatically brought along the common file!  Have fun!  :)

---

### Post by L Campbell on 2009-03-16
> **taurus said:**
> You have only installed skype-common, not skype itself.  Do you see the square box on the left that is not blue?  No blue, not installed.

So click skype and install it.

OK, I'm trying this but getting this error message.

---

### Post by taurus on 2009-03-16
Why don't you remove skype-common first.  Then, Refresh the list and try installing **skype** again.

---

### Post by L Campbell on 2009-03-16
> **taurus said:**
> Why don't you remove skype-common first.  Then, Refresh the list and try installing **skype** again.

Thank you very much, that did the job and I now have the Skype icon under 'Internet'.

I really appreciate all your time and patience.

Kind regards.

---

