---
title: "Midori"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-27
I am running Lubuntu 11.04 and because of the problem i've had with Firefox not starting i decided to install the Midori browser via synaptic. Midori installed without an hitch but when i went to menu => accessories and clicked on midori an error appeared.

Error-
file://usr/share/ubuntu-artwork/home/index.html

Could anyone out there tell me how i might get around this problem please.

---

### Post by nothingspecial on 2011-06-27
I think midori is trying to open a file that doesn't exist.

Change the homepage in midori's preferences to your favourite website.

---

### Post by Old-un on 2011-06-27
But i can't open Midori? When i do try to open Midori the error message appears.

---

### Post by TeoBigusGeekus on 2011-06-27
Create the file yourself; create the necessary folders yourself, if needed.
The file could be an empty file or a saved html page.

---

### Post by yetiman64 on 2011-06-27
You could try installing the ubuntu-artwork package (midori is refering to a file installed by it).
This package will draw in 4 other packages one of which supplies the index.html file midori is looking for.

```
sudo apt-get install ubuntu-artwork
``` Then try opening midori again and changing the homepage. **Edit:** once midori opens go to Edit > Preferences > General to change the homepage from the file.

Once the midori homepage is changed you could probably then get away with uninstalling the ubuntu-artwork and removing the packages it drew in.

```
sudo apt-get purge ubuntu-artwork && sudo apt-get autoremove
``` will do the removal and cleanup. With this removed and the homepage changed midori should work ok.

Note you will have downloaded deb files in /var/cache/apt/archives, if you wish to remove them as well,
```
sudo apt-get clean
``` though this last step is not entirely necessary and will clean out all previously downloaded installer packages, but it will free up a little disk space.

---

### Post by jerrrys on 2011-06-27
i just loaded Midori to see if its buggy out of the box. and its not, will need some tweaking though.  anyhow, Teo has the right idea.

EDIT: yetiman's post wasn't there when i tried this and posted.  so sounds good too

---

### Post by Old-un on 2011-06-27
I did try yetiman64's solution and unfortunately it didn't work. So i have decided to uninstalled Midori and have since installed the Chromium web browser which works great.

Thanks for all the replies and help though. Cheers

---

### Post by shuttleworthwannabe on 2011-06-27
Another suggestion for light weight distro's and web browser--why not install Chromium-it is light and fast, and it is in the repo's; it gets updated as well.

---

### Post by crispy_420 on 2011-06-27
From the command line (terminal) try this to get you in and edit from there:

midori [http://www.google.com](http://www.google.com)

After a successful connection it will setup a config file here: /home/username/.config/midori/config. You can edit this later by hand if needed to change the home page.

---

