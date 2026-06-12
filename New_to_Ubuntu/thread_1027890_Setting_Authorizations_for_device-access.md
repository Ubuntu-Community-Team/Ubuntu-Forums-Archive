---
title: "Setting Authorizations for device-access"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Astrodan on 2009-01-01
Hello,

I'm using Hardy Heron on an AMD64 and need to allow direct access to the parallel port for a program.  Can someone help out?  

I have tried adding the user to the lpadmin group.
I have looked at System > Administration > Authorizations.
I have tried to look and understand udev rules.

And, I should mention it works fine using Sudo or logging in as Root, but, I need this to be for users which are Desktop users and which I can specify if possible.

Thanks in advance, 
Dan

---

### Post by Michael.Godawski on 2009-01-02
Hm, 

> and need to allow direct access to the parallel port for a program

Do you mean you want to allow a specific user to be able to run an application without the sudo password?

Why if I may ask? What do you mean by parallel port in this context? (I am learning something new perhaps:D?)

Have a look at the sudoers file first, but it only should be altered if you really know what you are doing. Wrong entries can make your system crash.


[LIST]
[*][https://help.ubuntu.com/community/Sudoers#Introduction](https://help.ubuntu.com/community/Sudoers#Introduction)
[/LIST]

Here is also a nice example with many possible variations of the entries in the sudoers file; so you can get a picture what is possible with this method and what not:


[LIST]
[*][http://www.gratisoft.us/sudo/sample.sudoers](http://www.gratisoft.us/sudo/sample.sudoers)
[/LIST]

---

