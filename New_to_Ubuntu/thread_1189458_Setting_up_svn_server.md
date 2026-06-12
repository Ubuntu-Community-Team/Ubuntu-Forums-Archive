---
title: "Setting up svn server"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by vertex78 on 2009-06-16
I have a ubuntu lamp server setup and i installed subversion and libapache2svn.  Next I modified /etc/apache2/mods-available/dav_svn.conf and set it to this:

```


<Location /svn>

 DAV svn
 SVNPath /var/svn
</Location>

```

So next I tried checking out the repository without giving a username from another computer on my network and it worked. How do I make it ask for a password?

---

### Post by vertex78 on 2009-06-16
bump

---

### Post by DougB1958 on 2009-06-16
Take a look at the free Subversion book at [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/) if you haven't already. There's also a very active Subversion users mailing list at [email]users@subversion.tigris.org[/email] (I follow that list enough to know that they frequently deal with the kinds of set-up issues you're facing, but I don't follow those discussions closely enough to know the answer to your question.)

Good luck!

---

