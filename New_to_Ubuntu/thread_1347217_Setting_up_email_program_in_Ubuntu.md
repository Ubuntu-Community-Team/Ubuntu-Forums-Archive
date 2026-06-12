---
title: "Setting up email program in Ubuntu"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by rootytooty on 2009-12-05
I set up many email sets ups over the years in different OS. Even with the Easy mode on Xandros.
 
I am having a bit of a probem on my new Ubuntu 9.10. I have it receiving just fine but I can't get it to send. I have tried every combination that I can think of. Removed and installed my email several times.
 
As far as I know I have it set up correctly unless I am missing something that I just can't seem to see.
 
I have comcast and the sending server is smtp.comcast.net. I just can't seem to send my email.
 
My web browser works just fine also. Evalution is the email program. I had Thunderbird on my Xandros.
 
I really, really like Ubuntu but just need to fix this email problem.
 
Any suggestons please????
 
Thanks,
Bob

---

### Post by stoogiebuncho on 2009-12-06
If you prefer Thunderbird, it's easy to install in Ubuntu.  Just go to Applications > Add/Remove Programs (or Ubuntu Software Store, depending on your version), search for thunderbird, and install it.

Or, if you prefer to use the terminal, simply type
```
sudo apt-get install thunderbird
```

---

### Post by cartisdm on 2009-12-06
Just to double check that you're following all the right settings, compare what you've been doing with the steps given in this guide:

[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution)

EDIT:  Just for kicks, double and triple check your username.  sometimes it's something simple like @googlemail.com instead of @gmail.com

---

### Post by rootytooty on 2009-12-06
Thunderbird doesn't show up in the list of program downloads.

When I used the Terminal mode and use the sudo ...........   it tells me that there is no Thurderbird program.

I am using 9.10 

I have checked and double checked my settings and I can only  think that the ports might be wrong as they have to be changed from the normal settings.

Also, I might need to change the port number for my email settings.  How do I find the place to do that in the email settings please????

Thanks,
Bobby

---

### Post by plucky on 2009-12-06
> Also, I might need to change the port number for my email settings. How do I find the place to do that in the email settings please????


```
pop.comcast.net:465
smtp.comcast.net:995
```

will give you port 465 for pop and port 995 for smtp.Change for whichever port you need.


Good Luck

---

### Post by 3rdalbum on 2009-12-06
> **rootytooty said:**
> Thunderbird doesn't show up in the list of program downloads.

When I used the Terminal mode and use the sudo ...........   it tells me that there is no Thurderbird program.

I am using 9.10

Check that all the repositories are enabled in the Software Sources program, and hit Reload in Synaptic if necessary.

As for your e-mail problem, try changing the "Authentication type" settings for your e-mail account in Evolution.

---

### Post by benjamonk on 2009-12-06
> **rootytooty said:**
> 
 
As far as I know I have it set up correctly unless I am missing something that I just can't seem to see.


Hi Bob - I hope this isn't patronising, but are you 100% sure you've got smtp authentication set up exactly right on send email?

Always worth a double check.

---

### Post by rootytooty on 2009-12-07
I don't think you are patronizing at all.  I always appreciate the information.  That is what I have been playing with but I sure could have missed something.  I am putting in smtp.comcast.net, server requires authentication, no encryption,  use secure connection--no encryption, authentication plain, user name my email address and remember password checked.  Have I missed something please???

Does anyone know how to access the port settings so that I can put in my Comcast Port numbers please????

Thanks,
Bobby

---

### Post by plucky on 2009-12-07
> Does anyone know how to access the port settings so that I can put in my Comcast Port numbers please????

In Evolution **Edit > Preferences > Select Account > Edit > Sending Email/Receiving Email**

Good Luck

---

