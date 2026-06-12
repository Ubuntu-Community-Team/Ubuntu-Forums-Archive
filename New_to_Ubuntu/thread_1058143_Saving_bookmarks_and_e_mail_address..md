---
title: "Saving bookmarks and e mail address."
date: 2009-02-02
forum: New to Ubuntu
---

### Post by johnnybigs2000 on 2009-02-02
Hi All,

Been using Ubuntu for a while now but still consider myself as a Newbie.
I have been really pleased with the operating system.

I want to upgrade to the latest Version of Ubuntu.
It looks the only way is to reinstall Ubuntu's latest version.
The upgrade function does not work properly anymore.

I have Hardy heron right now.
I want to be able to copy and save My bookmarks and e mail address's  
So I can use them on the new install.
I am sure there is an easy way to do this.
Can somebody here help me out?

Thanks and look forward to your reply.

John

---

### Post by yeats on 2009-02-02
Hi John,

If you're referring to your firefox bookmarks and other profile information, they are stored in a hidden directory in your home folder called .mozilla.  Your email client also has a folder, either .thunderbird or .evolution or the like (you should be able to set Nautilus to view hidden files, or alternatively, open a terminal and type

```
ls -a
``` to see them)

The best way to preserve those settings is to back up your entire /home directory to external media, then you can copy it back into your new installation (or copy those directories piecemeal).

Hope that helps.

Chris

---

### Post by Therion on 2009-02-02
To save you Firefox bookmarks either use the [Foxmarks](http://www.foxmarks.com/) plugin (easiest way IMO) or go to Bookmarks/Organize Bookmarks/Import and Backup and select "Backup".  It'll dump your favorites to an .html file you can then import back into your fresh install of Firefox when you upgrade.

---

