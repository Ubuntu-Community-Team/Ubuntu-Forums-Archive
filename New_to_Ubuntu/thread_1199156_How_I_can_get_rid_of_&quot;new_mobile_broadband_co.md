---
title: "How I can get rid of &quot;new mobile broadband connection wizard&quot; on every startup?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by legolas_w on 2009-06-28
Hi
Thank you for reading my post
Everytime that I turn my laptop on it shows a wizard to help me go trough some steps to create a new mobile broadband connection.

Is there anyway to stop this wizard from showing off everytime?

Thanks

---

### Post by rraj.be on 2009-06-29
Try to remove it from Startup applications.

System-->Preference-->Startup Applications.

There select that application and click on REMOVE.

Thats it.

---

### Post by lavezarez on 2009-07-15
> **legolas_w said:**
> Hi
Thank you for reading my post
Everytime that I turn my laptop on it shows a wizard to help me go trough some steps to create a new mobile broadband connection.

Is there anyway to stop this wizard from showing off everytime?

Thanks


I had the same problem. I tried the incomplete advise of rraj - you didn't tell us what to disable in the preferences - there are so many startup applications in the list, so i guessed it to be network manager.
This caused the wizard to stop everytime I start-up, but it also made my network connection icon to totally disappear from my panel.

What I did to correct the problem was this:
1. Placed back Network Manager in my startup apps.
2. Logged off, then logged in again to my account
3. When the wizard appeared, I clicked Forward, to create a second copy of the mobile broadband.
4. Edited the connection properties (right-click the network icon, select Edit Properties, then pick the newly-created broadband connection)
5. Checked the **Connect Automatically**, and Unchecked the **Available to all users**
6. Deleted the old mobile connection after copying its settings to the 2nd copy.

Then I restarted this, and the wizard was gone, but my network icon still in the panel :)

I had to repeat these steps for all the users configured in my Ubuntu PC, bec. the wizard popped up to all the user logins.

---

### Post by lisati on 2009-07-15
> **rraj.be said:**
> Try to remove it from Startup applications.

System-->Preference-->Startup Applications.

There select that application and click on REMOVE.

Thats it.

In addition to this, I'm wondering what happens if the other posters fill it in, even with "dummy" or "nonsense" values, and let it run to completion.

Another thing, is there a mobile phone or USB mobile modem plugged in when the laptop is turned on?

---

### Post by mariano.j on 2009-07-19
Try backlisting the kernel modules cdc_acm and cdc_wdm and keep them from loading at startup:

```
echo -e "blacklist cdc_acm\nblacklist cdc_wdm" | sudo tee -a /etc/modprobe.d/blacklist
```Caveat: may cause problems with hibernate and standby function. Try this.

@legolas_w
Does this solve your problem?

---

### Post by 3rdalbum on 2009-07-19
The computer probably has a 3G modem built-in. Just fill in dummy information into that wizard and you'll never be bothered again.

Yeah you could blacklist the modules as mariano.j said above, but you must remember what you did in case you ever get mobile broadband and you want to use the 3G modem!

---

### Post by ugm6hr on 2009-07-19
> **3rdalbum said:**
> The computer probably has a 3G modem built-in. Just fill in dummy information into that wizard and you'll never be bothered again.

Sensible advice.

---

