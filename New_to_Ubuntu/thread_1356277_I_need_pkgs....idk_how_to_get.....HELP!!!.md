---
title: "I need pkgs....idk how to get.....HELP!!!"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by princessalisi on 2009-12-15
My computer keeps telling me I need different packages to download frostwire. It says I need things like "Sudo Pkg"....or i need to use my "update Manager" and something like "aptitude" I really dont know whats going on.
I have never used Ubuntu before this so I dont really know what to do any help would be great!!!

---

### Post by ramjet_1953 on 2009-12-15
Hi, there!

If you follow this link and read through it, it should help.
If you have any follow-up questions after reading, just post them.

[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

Regards,
Roger :)

---

### Post by princessalisi on 2009-12-16
Ok well anytime i try to do anything with my package manager or my synpatic package manager it tells me this [SIZE=3][B]"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
[/B][/SIZE]
so idk what that means.....it doesnt help that i know nearly nothing about computers.

---

### Post by cenzorrll on 2009-12-16
what it's telling you to do is enter that command into a terminal (known as command line in windows)  in this case you can copy and paste the "sudo dpkg ...etc" line and run it (ctrl-shift-v pastes in the terminal, not ctrl-v, same goes for copying) 

SO:

go to applications>accessories>terminal   and insert the command and press enter, it should do everything on it's own.

i would highly suggest learning a few basic commands that can be run in the terminal, it's extremely fast and very powerful.  you'll also be able to recognize when someone may give you a very dangerous command (beware of anything starting with "sudo rm" or even "rm" unless you know what you're doing)

---

### Post by princessalisi on 2009-12-16
so this may sound like a dumb question but like a said dont know alot about computers so is this what i paste there?.... [SIZE=3][B]"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/B][/SIZE]

---

### Post by cenzorrll on 2009-12-16
just: 

```
sudo dpkg --configure -a
```

---

### Post by princessalisi on 2009-12-16
Thank you I believe its working!.......I think I LOVE YOU!! LOL

---

### Post by theozzlives on 2009-12-16
You can get frostwire [here]("http://www.getdeb.net/welcome/") Just download the *.deb file, then double-click on it.

---

### Post by princessalisi on 2009-12-16
Thank you theozzlives that helped alot!

---

