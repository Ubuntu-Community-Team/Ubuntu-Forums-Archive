---
title: "Tk load error on Ubuntu"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by diabolator2 on 2009-12-21
Hi all! I start using Tk to create Ruby GUI apps but that's da error:

diabolator2@book:~$ cd /home/cristi/Desktop
diabolator2@book:~/Desktop$ ruby firsttk.rb
firsttk.rb:1:in `require': no such file to load -- tk (LoadError)
  from firsttk.rb:1
diabolator2@book:~/Desktop$

I tried to reinstall Tk but it was ok:

diabolator2@book:~$ sudo apt-get install tk
Reading package lists... Done
Building dependency tree
Reading state information... Done
tk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

what's up?
Thanks!

---

### Post by milosz.galazka on 2009-12-21
Missing libtcltk-ruby?
[http://www.ruby-forum.com/topic/200938](http://www.ruby-forum.com/topic/200938)
[http://ruby.about.com/od/tk/a/Tk.htm](http://ruby.about.com/od/tk/a/Tk.htm)

---

### Post by diabolator2 on 2009-12-22
I guess you might be right. I'll try. Thanks.

P.S.: why can't THEY create a pack with all needed inside? I thought a "sudo apt-get install tk" command would be enough... In XP it could be a doubleclik installer. Install and forget... The only thing I dont wanna get back to XP is that I won't give up with Linux. any, quite any install process s*cks!

---

### Post by milosz.galazka on 2009-12-22
After installing tk you can use it but using it from ruby/... requires bindings. The same rule applies to other libraries like gtk, qt and so on.

---

