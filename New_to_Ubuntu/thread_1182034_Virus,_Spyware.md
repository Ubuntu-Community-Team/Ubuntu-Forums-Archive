---
title: "Virus, Spyware ??"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by freeediver on 2009-06-08
Something weird today and I'm not sure what to do or why it happened.
Today Every website on my favorite list has required me to re-login.
I get directed to my login page, my information is all there
all I am required to do is hit enter.
This is weired, what's up and how do I check?
I am only using Ubuntu, I do not have a dual boot setup.

Thanks

---

### Post by AutumnPhoenix on 2009-06-08
did you recently clean cookies?

---

### Post by freeediver on 2009-06-08
nope no changes on my end.

---

### Post by joyneo04 on 2009-06-08
What browser are you using???

---

### Post by CJ Master on 2009-06-08
There are no Viruses or spyware in the wild for Ubuntu at this point of time. It is still possible to get a trojan horse, although I doubt this is the case.

I can't help you with why this is happening, but does it happen everytime you restart your browser or just that once? If it happens every time you restart your browser then it's set to clear cookies on shutdown.

---

### Post by Junkieman on 2009-06-08
Hi, if you're using Firefox, the default web browser in Ubuntu, go to Edit -> Preferences, and on the Security tab there's an option "Remember passwords for sites". Is this checked? If so then that explains why all your login info is automatically populated into the user name + password fields on web pages, assuming you chose to 'Remember' the login details for them. If it's not checked, look if you have any Firefox add-ons installed that manage your passwords: Use the Tools -> Add-ons menu, and look in the Extensions tab.

Also check on the Privacy tab in Preferences, there's an option to "Always clear my private data when I close Firefox", if this is checked then it might explain why you need to re-login.

When logging into a site, always make sure the URL in your address bar is for the site you want, and not a fake URL.

---

### Post by freeediver on 2009-06-08
I checked, everything is already checked or not checked ( clear info.) as advised. I still have the issue, even here I was directed to the log in page and it had my info. I just needed to hit enter.
Forgot, yes I am using Firefox.

---

### Post by Junkieman on 2009-06-11
> **freeediver said:**
> I checked, everything is already checked or not checked ( clear info.) as advised. I still have the issue, even here I was directed to the log in page and it had my info. I just needed to hit enter.
Forgot, yes I am using Firefox.
I'm not too clear on what you're trying to say, but it sounds like everything is fine IMO.

When you log in to a site, like these forums, check the "Remember Me" box. It just sounds like your session gets cleared when you close your browser.

---

### Post by jperez on 2009-06-11
Are you using NoScript or just recently installed it?

Jesse~

---

### Post by freeediver on 2009-06-11
Nope no changes that I know of other than a Fire Fox update
a couple weeks ago. I don't think that was it because everything still worked normally after the update for about a week.
Yes it seems everything gets cleared after every shutdown even tho
I select remember me. Every setting I have checked still says my log in information should be remembered.
I finally gave up and did a complete re-install, everything works now I just need to reload some programs. Google earth is the stinker now but thats a different thread.

---

### Post by philinux on 2009-06-11
For google earth. Easy peasy install.

Click the medibuntu link below and follow their instructions.

Then googleearth will be available to install from add/remove synaptic or

from firefox address bar thus

apt://googleearth

---

### Post by freeediver on 2009-06-11
I tried this and the D/L works fine however when I try to open GE
my system crashes and restarts.
I get some info for about one sec. It splashes up on a black screen
and  says something about boot, is there any way to hold this screen so I can read it?
GE worked fine until I completely re-installed my system, I had a HD error.
Thanks for your help.

---

### Post by philinux on 2009-06-12
Open a terminal and run it from there. You'll then get the error messages.

```
googleearth
```

---

### Post by Junkieman on 2009-06-12
> **freeediver said:**
> I tried this and the D/L works fine however when I try to open GE my system crashes and restarts.

Wow thats some problem :p What GFX libraries does Google EArth use, SDL? 

First guess is to check your graphics card, do you know what hardware you have, and are you using proprietary drivers? In a terminal run lspci to see what you have. 

Also look in the menu **System -> Administration -> Hardware Drivers** to see if you have any installed, and enabled?

---

### Post by Viva on 2009-06-12
Most likely the browser crashed while closing and lost its cookies. Did you choose to remember any passwords?

---

### Post by freeediver on 2009-06-12
For programs such as GE I always select to save passwords.
It seems lots of others are having the same issues.
Last year when I installed GE 4.2 I had issues installing it as well but finally got it working. To do that I must have read a few 
doz. threads and fixes, all lost now with my re-install.
It did work with my current graphics card no reason it should not continue to do so.
Thanks for all the ideas, I'm sure one will work.
I have a new thread on my GE issue.
<<>>

---

