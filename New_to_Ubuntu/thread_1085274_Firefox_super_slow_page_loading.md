---
title: "Firefox super slow page loading"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by AgentXSmith on 2009-03-02
Installed some firefox packages a few days ago (procrastinating) and now it takes forever to load up a page.  Checked the error console and it is just brimming over, dozens and dozens of repetitive errors every time I try to load a new page.  I believe that's what slowing it down.  Any fix for this other than going to Opera or something?

Here's a few examples of the errors:

Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css)
Line: 501

Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css)
Line: 506

Warning: Expected color but found '#'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-358373b8-00098.css)
Line: 1023


And just on and on...

---

### Post by Sysero on 2009-03-03
Hmm...

This may sound strange, but in the Firefox menu, go to:

[COLOR="Navy"]Edit - Preferences - Content[/COLOR]

Look and see if the [COLOR="Navy"]Load Images Automatically[/COLOR] box is checked.  If not, check it and restart Firefox.

See if it helps.

---

### Post by AgentXSmith on 2009-03-03
It's checked.  I'm not getting errors just for images, it's nearly line for line that it finds a problem.  Always says "Declaration dropped" at the end of the error.  What does that mean?

---

### Post by philinux on 2009-03-03
Open a terminal and run this.

firefox -safe-mode

---

### Post by AgentXSmith on 2009-03-03
^OK, did that.  Still getting beau coup error messages, though it seems it's running a bit quicker.

---

### Post by Sysero on 2009-03-03
Hi.

The reason I asked earlier about "Load Images Automatically" is that a friend updated Firefox, got the same errors as you and checking the box fixed it.  

Anyway, what version of Firefox are you running and what packages (or do you mean "add-ons") did you install?  If we know these things, we can start FF in safemode and look for the problem.

---

### Post by Sysero on 2009-03-03
There is one thing that you could do until we figure out what's going on.  We could create a new profile in FF for you to use.  Here's what to do.  First you have to close firefox copy and paste this to a text file for reference.

Open a terminal.

Type:

```
firefox -ProfileManager
``` 

When the profile manager opens, click [COLOR="Navy"]Create Profile[/COLOR].  After you create a name for your profile, before you leave the Profile Manager, make sure the [COLOR="Navy"]Don't ask at startup[/COLOR] box is unchecked.

When you restart Firefox, you will be given a choice of profiles to run.  Choose your new one.  Browse around for a while.  If it works, at least you have a working FF browser until we can solve the problem.

---

### Post by scottuss on 2009-03-04
Type about:config into the address bar then search for ipv6 in the filter bar, when you see the entry for network.dns.disableIPv6 make it "true" by double clicking on it.


That disables ipv6 which can cause Firefox to go slow. Let us know how it goes.

---

### Post by AgentXSmith on 2009-03-12
I've done the about:config thing and set up a profile (unchecked the don't ask me box) and I'm still getting all the error messages.  The bright side is that I've determined the slow page loading to a connection problem, not the endless error messages.  Still, it would be nice to know why they occur.

---

