---
title: "[SOLVED] Apache ignoring symlinks"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by luke16 on 2008-07-06
I've been trying to put up some files on a home server using apache2, however, the files are large, so I linked them, and then gave the target permissions, along with the public_html folder and all the files in it, but for some reason, links are still invisible on the actual webpage. I even tried putting in "Options FollowSymLinks" in my sites enabled for my pub html dir, but it still won't work. Does anyone know how to get apache to not ignore links?

---

### Post by HalPomeranz on 2008-07-06
"FollowSymlinks" is definitely what you want, so I'm surprised it's not working for you.  Did you restart the web server after updating the config file with this option?  

Have you checked the permissions on the files that the symlinks point to?  Perhaps they're not readable by the web server user or they're in a directory that's not accessible to the web server user?

---

### Post by luke16 on 2008-07-06
> **HalPomeranz said:**
> "FollowSymlinks" is definitely what you want, so I'm surprised it's not working for you.  Did you restart the web server after updating the config file with this option?  

Yes. I believe I was using "/etc/init.d/apache2 restart".

> **HalPomeranz said:**
> Have you checked the permissions on the files that the symlinks point to?  Perhaps they're not readable by the web server user or they're in a directory that's not accessible to the web server user?

Wouldn't that just mean that you would get an access forbidden error? Mine aren't even showing up.

I am including my configuration files. Maybe you can see whats wrong? In the sites-enabled folder, right now I have     <Directory /home/*/public_html/>
        Options Indexes FollowSymLinks
    </Directory>

---

### Post by HalPomeranz on 2008-07-06
Ah.  Your problem is that you have "FollowSymLinks" set in apache2/sites-enabled/default but "SymlinksIfOwnerMatch" set in apache2/mods-available/userdir.conf.  You should remove the userdir configuration lines from apache2/sites-enabled/default and do your settings in apache2/mods-available/userdir.conf instead.

---

### Post by luke16 on 2008-07-07
Okay, so I edited the mods-available/userdir.conf to this:
```

<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit
                Options MultiViews Indexes FollowSymLinks IncludesNoExec
        </Directory>
</IfModule>

```while getting rid of the the user dir config from the sites-enabled config, and then restarted apache2,```
sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
``` but my site is still only showing the files that are physically in the folder when I view [http://127.0.0.1/~luke/]("http://127.0.0.1/%7Eluke/") with firefox.

EDIT: Okay, it is now working. It seems to have been a permission problem. Apparently, you need to have both the link and the folder set as executable? Or maybe I was negligent in setting the read permission to others. I will have to play with it to see. Thanks for the help.

---

### Post by luke16 on 2008-07-07
It looks like the problem is that I have to not only give the parent folder of the target "access files" permission, but also the grand-parent. So not only the foo from ~/pics/foo/bar.jpg, but also the pics as well for bar.jpg to become visible.
My question here is, how safe is giving "access files" permission to my main pics directory? Will only stuff that I link to be visible? Will people only be able to read the files and the folder contents (including subfolders and their contents) that I link to, or is there a way to get access to the non listed stuff?

---

### Post by HalPomeranz on 2008-07-07
The only thing people will be able to access via your web server is the files you've explicitly linked into your ~/public_html folder.  People using the web server shouldn't be able to browse your homedir outside of this directory.

---

