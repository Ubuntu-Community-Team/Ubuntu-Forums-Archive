---
title: "Samba in ubuntu"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by navaneethan on 2009-07-08
Hi all,

       I need to know how to use samba in ubuntu?

       What we ve to do?

       detaily!! plz

---

### Post by ainsworth_t on 2009-07-08
There are a lot of useful sections in the Ubuntu Server Guide:

[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

Also check out the community documentation:

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by alexlafreniere on 2009-07-08
Are you comfortable working with config files, or do you want to use a GUI? There are tons available for Samba, if that's how you like to work. Check out this page for more info: [http://us1.samba.org/samba/GUI/](http://us1.samba.org/samba/GUI/)

---

### Post by issih on 2009-07-08
Given you are posting in absoltue beginners I'm going to break from the above posters assume you are running the desktop version of ubuntu.

If you want to share files using samba using ubuntu just open up the file manager and right click on the folder you want to share, in that pop up menu select the sharing options and then set up the share as you want.

The first time you ever do this the system will then need to install a some new packages, just follow the instructions in the dialogs that it brings up, and enter your login password when required. (N.B, I know this happend in intrepid ibex, I can't honestly remember for jaunty whether it need to grab new packages at this point or not, it may come preloaded)

Once that is completed you should have samba set up, and you just configure shared folders by right clicking on them. 

You can view other machines shared folders from the network link in the places menu or the file browser.

its that simple....hopefully :)

Hope that helps

---

