---
title: "Help to chmod correctly a web server"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by jordi_rc on 2007-03-18
Hello

I have a web server in my PC. I need to chmod the files correctly so I don't have a security risk.

I am using a CMS for the website.
I have full access to my pc, as it is in my house, and I can manipulate it through keyboard, so I have no problem to change the chmod to the most restrictive ones.

I have these:

1) The config file, wich I chmod 444. This way is readable for all, but can't be executed or writen. What does this mean? People can read the password and user and other data there? Should I chmod that to 400 ? So no one, except me, can read it?

2) The folders that users need to write to. For example where they upload the images or files that are public. I should chmod them to 777. Is this right?

3) The rest of the website folders. I think they are well chmod 755. This means I can write, and the other can open or execute.

I think this is not a good setup. Maybe, I can do a more restrictive setup that permits all people look the website, use it.
Remember, I have those 3 pieces: the config, the users folders and the rest.
Are those chmod ok?
Should I do a different chmod for files and folders?
How?

Thanks

Jordi

---

### Post by gradedcheese on 2007-03-18
The first thing I would do is find out what user your CMS runs under.  If it's a PHP application, find out what user PHP gets run under, etc.  You can then chown appropriately and set user and owner permissions more intelligently.  There's a significant different between ways PHP is set up for example, some servers have it run under 'nobody', while others have it run under a real user.  Issues come up like this: if 'nobody' creates and owns files (that only it has permissions to r/w), you might be sort of locked out of those files.

---

### Post by jordi_rc on 2007-03-18
Hello

The CMS is Drupal.
It has a superuser that is the admin.

Do you have some sugestion?


Thanks for reply

Jordi

---

### Post by jordi_rc on 2007-03-19
I asked on Debian and they said me:

444 for config file.

744 or 644 for its folder.

777 for the folders that need to be written by the server or the people.

755 for other folders, and if I have no Perl script, only PHP, I can use 644 too.

Jordi

---

