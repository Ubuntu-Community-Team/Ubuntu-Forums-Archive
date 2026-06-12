---
title: "Permissions???"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by planegenius on 2009-04-13
I just ditched windows xp and installed ubuntu 8.10 ;).  However, I can't get online, because I need to edit some core things as described in these blog posts-

[http://sin613.blogspot.com/2007/02/i-win-again.html?showComment=1182281400000#c6458705645854986674](http://sin613.blogspot.com/2007/02/i-win-again.html?showComment=1182281400000#c6458705645854986674)

[http://sin613.blogspot.com/2007/02/i-win.html](http://sin613.blogspot.com/2007/02/i-win.html)

My questions to you are:

-How do I edit hostap_cs.ko and where is it?

-Right now, I can't edit interfaces because 'i don't have permission', how can i get permission to edit this?

Thanks!

---

### Post by HalPomeranz on 2009-04-13
DO NOT follow the advice in the postings that you refer to in your message.  They're for a very old version of Ubuntu and surely don't apply to the version that you're running.  Wireless interfaces are now managed via NetworkManager.  You'll find the icon in the upper-right corner of your desktop-- look for the thing that looks like two computer displays stacked on top of each other and left or right click to bring up different menus.

To answer your other question, if you want to edit a file with administrative privileges, right click the file in your file browser. Select "Open With > Open with Other Application...".  Then select "Use a custom command" and enter "gksu gedit".  That will prompt you for your login password, then start the simple text editor with administrative privileges.

Or from the command line: "sudo gedit <filename>"

Or from the command line with a non-graphical text editor: "sudo pico <filename>"

---

### Post by planegenius on 2009-04-13
Thanks so much!

I decided to just stop trying to fix that and am looking in to getting another adapter.

Can you help me pick one? 
[http://ubuntuforums.org/showthread.php?t=1125008](http://ubuntuforums.org/showthread.php?t=1125008)

Thanks again!

---

