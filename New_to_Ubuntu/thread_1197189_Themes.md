---
title: "Themes"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-06-25
ok i went to this web page and i followed the steps and downloaded the package for the new theme for ubuntu. followed the steps and when i do the command *[COLOR=#800000]cd Mac4Lin_v1.0_RC1 in terminal i get a error that the directory could not be found.  when i type in the right folder that it named it will cd to it. but then it cant open the next file on list which is [/COLOR]*[I][COLOR=#800000]sh Mac4Lin_Install_v1.0_RC.sh.  can anyone put this page in simple english for me to upgrade my theme please.  the page i got the instructions form is 


[http://www.info123.org/tutorials/57-how-to-make-your-ubuntu-jaunty-look-like-mac-os-x-leopard](http://www.info123.org/tutorials/57-how-to-make-your-ubuntu-jaunty-look-like-mac-os-x-leopard)

Thank you for your help.
[/COLOR][/I]

---

### Post by Bachstelze on 2009-06-25
Where did you save the theme archive to, and how did you extract it?

---

### Post by ad_267 on 2009-06-25
Ok firstly, that is a terrible guide. Any guide telling you to use sudo to create directories in your home directory is just plain bad.

The file and directory names on that site look outdated, you should be able to extract that archive, then use:
```
cd Mac4Lin_Install_v1.0
./Mac4Lin_Install_v1.0.sh
```

---

### Post by Leshinsky on 2009-06-25
i saved it to "matthew" which i believe is home folder and i extracted it with file roller 2.26.1 An archive manager for GNOME. which was just the default extracter.

---

### Post by ad_267 on 2009-06-25
The commands I gave should work then. I haven't tried the script myself though. It looks like it changes a lot of things other than just the GTK themes, so you could just apply the GTK themes yourself  if that's all you want (GTK themes set the look of controls in most applications in Ubuntu).

You can go to system - preferences - appearance - themes and browse to the Mac4Lin_Install_v1.0 directory, then into the GTK directory and drag the .tar.gz files in that directory onto the theme window to install them. You can also do the same for the file in the Icons directory.

This guide doesn't relate directly to the Mac4Lin theme but might be useful: [http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

---

### Post by Leshinsky on 2009-06-25
so maybe you will know what im talking about and maybe ill have you totally lost.  but i want there to be that bar with the programs on the bottom and i want the file menus to act like a mac so basically you cant tell the difference between this and a mac. like i saw on [http://ubuntu.hamdi.web.id/](http://ubuntu.hamdi.web.id/)  i want my computer to look like the second one down.  titled [GTK Leopard Ubuntu Theme]("http://ubuntu.hamdi.web.id/themes/gtk-leopard-ubuntu-theme.html") but that is more confusing that the other post on how to do it.  any ideas.  the attached picture is what my desktop looks like after doing those two commands and i want it to look like that site.  any ideas.

---

### Post by ad_267 on 2009-06-25
I think you want Global Menu and AWN.

Global menu gives you the File, Edit, Tools etc menus in the top panel and is available from [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/).

AWN is the dock down the bottom. There are instructions for installing it at [https://help.ubuntu.com/community/AvantWindowNavigator](https://help.ubuntu.com/community/AvantWindowNavigator).

---

### Post by Leshinsky on 2009-06-25
any other ideas that dont want to work on my system.

---

### Post by ad_267 on 2009-06-25
Why won't it work? What error do you get? I'm pretty sure it should work.

---

### Post by Leshinsky on 2009-06-25
It just does a general error when i try to add the new source. then wont let me into package mgr til i reboot. any other ideas. or maybe another version of the theme that i can down load to do it all.

---

### Post by ad_267 on 2009-06-25
What's a general error? What's the exact error message you get?

---

### Post by Leshinsky on 2009-06-25
well i added the source but none of the files are in the package mgr

---

### Post by ad_267 on 2009-06-25
You have to click on the reload button for it to check the repository for new and updated packages.

---

### Post by Leshinsky on 2009-06-25
After adding that site to the reporitory and reloading it i get this error.

 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

---

### Post by ad_267 on 2009-06-25
You should still be able to install the package, that's just a warning. You can see here for how to add the GPG key for a PPA: [https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20using%20GNOME](https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20using%20GNOME)

---

### Post by Leshinsky on 2009-06-25
Problem is after i get that message the only option is to close it.  Then when i try to go into package mgr and find the three files to make my ubuntu look totally like mac the files arent there.

---

