---
title: "Silly Thunderbird/Enigmail problem"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by decoherence on 2011-08-07
I've gotta be missing something really obvious here. How do I disable default encryption in Thunderbird/Enigmail? I generally don't want to encrypt my mail but occasionally I forget to disable it and one gets out. How do I make it so I have to explicitly turn it on?

thanks,

---

### Post by Soul-Sing on 2011-08-07
make a user profile for thunderbird with gpg/pgp encryption and a one without encryption.

---

### Post by decoherence on 2011-08-07
I appreciate the response and investigated doing what you suggest however it seems like an awful lot of hassle just to change a default behavior. A significant amount of work has gone in to making my default profile work the way I want. Is there an easy way to copy all of the settings from one profile to another so that they are identical except for using encryption?

It seems a bit nuts that there isn't a preference to switch this when there are options to encrypt responses to encrypted email by default. Seems like this option should be right next to that.

Thanks again,

---

### Post by scheibenlosen on 2011-08-07
> **decoherence said:**
> I appreciate the response and investigated doing what you suggest however it seems like an awful lot of hassle just to change a default behavior. A significant amount of work has gone in to making my default profile work the way I want. Is there an easy way to copy all of the settings from one profile to another so that they are identical except for using encryption?

It seems a bit nuts that there isn't a preference to switch this when there are options to encrypt responses to encrypted email by default. Seems like this option should be right next to that.

Thanks again,

Have you tried running the setup wizard and making changes there? I'm in the process of setting up Enigmail (thanks for the reminder of something I should have already done :)), and working through the wizard, I got this:

[[IMG]http://img838.imageshack.us/img838/1949/enigmail2.th.png[/IMG]](http://imageshack.us/photo/my-images/838/enigmail2.png/)

and when I clicked on Next/Forward/whatever, I got this:

[[IMG]http://img651.imageshack.us/img651/5094/enigmail1.th.png[/IMG]](http://imageshack.us/photo/my-images/651/enigmail1.png/)

Does that help any?

---

### Post by Sergio.G on 2011-08-08
Hi, 

In Thunderbird's main menu, go to Edit, then Account Settings, select OpenPGP Security, there you will find the message composition default options.

I think you have to un-check the option: Encrypt messages by default  

Hope it helps
Cheers!

---

### Post by decoherence on 2011-08-12
Sergio, you are my hero. I've been looking for that option under the OpenPGP -> Preferences menu.

Thanks a lot!

---

