---
title: "phpmyadmin troubles"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by thorbs on 2011-03-30
I have succesfully installed lamp. Then I wanted to install phpmyadmin using the softwarecenter. When doing this something went wrong. It did not install probably, but it still installed. 

Now I wanted to uninstall it in order to make a proper install, but the softwarecenter makes the same error as before.

I am stuck, please help...

t.

---

### Post by Nerflander on 2011-03-30
Check out synaptic packet manager and search for phpmyadmin and see if you can remove the packages manually trough the manager.


installing phpmyadmin trough terminal works better btw.

---

### Post by stoogiebuncho on 2011-03-30
+1 for removing through Synaptic.  Make sure you right-click and select the option to completely remove, including configuration files.

Out of curiosity, what is the error message you're getting?

---

### Post by thorbs on 2011-03-30
Well i have been working with it all day, so I do not have the original error message. 

but now I am getting a 404 from the phpmyadmin. Every time I make a new installation, I have such trouble with the setup of lamp. Its unbelivable. The instructions seems clear and easy, but it always seems to be very hard in reality. Maybe I am Lamp cursed...

---

### Post by stoogiebuncho on 2011-03-30
If you somehow didn't configure phpmyadmin to work with apache (this is the step I always mess up, because it LOOKS like it's selected but it's NOT - you have to press the spacebar to select it), the problem might be as easy to fix as creating a link to phpmyadmin in your /var/www/ directory.

When you try to open phpmyadmin, I'm guessing you use a url like [http://localhost/phpmyadmin](http://localhost/phpmyadmin) or something like that, is that correct?

If that's not working, you can find your phpmyadmin directory, and make a soft like from that directory to your /var/www directory.  It's probably easiest in the terminal:

```
sudo ln -s /path/to/phpmyadmin/ /var/www/
```

---

### Post by stmiller on 2011-03-30
> **stoogiebuncho said:**
> If you somehow didn't configure phpmyadmin to work with apache (this is the step I always mess up, because it LOOKS like it's selected but it's NOT - you have to press the spacebar to select it), the problem might be as easy to fix as creating a link to phpmyadmin in your /var/www/ directory.

When you try to open phpmyadmin, I'm guessing you use a url like [http://localhost/phpmyadmin](http://localhost/phpmyadmin) or something like that, is that correct?

If that's not working, you can find your phpmyadmin directory, and make a soft like from that directory to your /var/www directory.  It's probably easiest in the terminal:

```
sudo ln -s /path/to/phpmyadmin/ /var/www/
```

Eek no don't do this. It's best to setup aliases and paths in apache config files. 

( See /etc/phpmyadmin/apache.conf for more details )

I would just remove completely as described in this thread, then reinstall.

---

### Post by thorbs on 2011-03-30
After some work I made it. The spacebar did wonders btw. apparently I was not marking appache probably. Thanks to all for the help.

t.

---

