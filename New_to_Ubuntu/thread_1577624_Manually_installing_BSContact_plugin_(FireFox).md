---
title: "Manually installing BSContact plugin (FireFox)"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by Tea-Man on 2010-09-19
Hi there,

I've downloaded the vrml-viewer BSContact and their site said it included both a standalone and a plugin.
Now, the installation went fine (as far as I can tell), and I can run BSContact standalone without a problem
But then the plugin part went wrong:
It didn't auto-install the plugin for sure, but I found a directory with plugins in /opt/BSContact (/firefox/plugins) that included BSContact.so and BSContact.xpt.
 I went to /usr/lib/mozilla/plugins and copy-pasted BSContact.so in there.

I tested it at this point and it seem to show properly in about:plugins, but when I went to an example-page ([http://www.bitmanagement.de/php-bin/ViewVrml.php?fullPage=yes&url=http://www.bitmanagement.de/developer/contact/vrml/doom/wrl/map01.wrl](http://www.bitmanagement.de/php-bin/ViewVrml.php?fullPage=yes&url=http://www.bitmanagement.de/developer/contact/vrml/doom/wrl/map01.wrl)) it didn't show a blank page like it did before, but... it crashed.

So, then went to /usr/lib/firefox-3.6.9/components and copy-pasted BSContact.xpt. But, of course, it still crashed when I tried the example.

I really have no idea how to manually install a FireFox plugin (don't know if it's possible, haven't found too much on the topic yet) and just pasted the file in places where there were files alike :P So I probably did something really stupid...

Well, any help on this would be really appreciated, thanks a lot!

BTW: I use Ubuntu10.4 and FireFox version 3.6.9

---

### Post by Tea-Man on 2010-09-21
*bump*

---

