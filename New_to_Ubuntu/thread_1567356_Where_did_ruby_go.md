---
title: "Where did ruby go"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by MontrealMike on 2010-09-03
Hi all,

I installed ubuntu last weekend 10.04 LTS.  As a windows user I am blown away by the ease of install and the quality of the software.

Now, my problem:

I just installed Ruby with: sudo apt-get install ruby1.9.1-full

The install seemed to work fine.  Now how do I start it?  The documentation says to type "irc" from the command line but that does not work.  No Ruby item can be found in th Gnome Applications menu.  "Find" does not find a file called Ruby (or irc).

Can anyone suggest something.

Thanks,

Mike

---

### Post by jimbob on 2010-09-03
Start synaptic from the menu and do a search on ruby.  If it is there, open a terminal window and enter locate ruby to find out what library it is in. If it is in the standard path, you should just be able to type the name in the terminal window and it will start.

---

### Post by MontrealMike on 2010-09-03
Thanks JimBob.  I had tried that but I looked harder this time.  It turns out that I have to start it using "irb1.9.1"!  The irb stands for Interactive RuBy.  I did not expect that.  

Cheers.

---

### Post by jimbob on 2010-09-03
I don't know anything about ruby or its use.  I have a command line that I have to run from a terminal window when some highly inconsiderate Windows user sends me an email with a .eml extension that Thunderbird cannot handle properly:

ruby eml2mbox.rb ./my_emls /home/jaspmatt/.mozilla-thunderbird/w7mlv8mo.default/Mail/"Local Folders"/Inboxmbox

I have no idea whether or not ruby has a graphical interface.

---

### Post by ratcheer on 2010-09-03
> **MontrealMike said:**
> Thanks JimBob.  I had tried that but I looked harder this time.  It turns out that I have to start it using "irb1.9.1"!  The irb stands for Interactive RuBy.  I did not expect that.  

Cheers.

Just create a symbolic link from irb1.9.1 to irb and you will be good to go. I am surprised the installation routine didn't create it for you.

Alternatively, you could create a shell alias.

Tim

---

### Post by tgalati4 on 2010-09-03
This allows you to install multiple Ruby frameworks.  You may have applications that are using older versions of Ruby.  To see all of your ruby stuff:

locate ruby
whereis ruby
apropos ruby

To see what versions of ruby that are readily available:

apt-cache search ruby

---

### Post by MontrealMike on 2010-09-07
Thanks everyone.  I am glad I posted this in the absolute beginner section!

---

