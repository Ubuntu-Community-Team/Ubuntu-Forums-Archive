---
title: "Help: Creating a Script"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by wickedcultgod on 2009-03-06
Hi all. I have installed Ubuntu Intrepid on my Acer Aspire One. There is a handy guide here : [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

There is only one thing I am having a  problem with. It says: 

QUOTE

Now you should create a script to restart the interface on awake from suspend mode, as it will otherwise hang. As root, create /etc/pm/sleep.d/00wireless 

UNQUOTE

How do I create this script?

---

### Post by Kinney on 2009-03-06
I haven't actually gone through this I'm just going by what the article you linked said.

First open the file(or create it if it doesn't already exist) to edit it. This command uses vim to edit the file but you can use whatever editor your comfortable with.
```
sudo vim /etc/pm/sleep.d/00wireless
```

Then in that file enter the following and then save it.
```

#
# Restart WiFi interface after suspension
#

case "$1" in
        resume|thaw)
                /sbin/ifconfig wifi0 down
                /sbin/ifconfig wifi0 up
        ;;
        *)
        ;;
esac

exit $?

```

Once you've done that you just need to make it executable by running:
```

sudo chmod u+x /etc/pm/sleep.d/00wireless

```

---

### Post by geirha on 2009-03-06
Alt+F2 to get the run dialog, then run ```
gksu gedit /etc/pm/sleep.d/00wireless
``` Type/paste in the lines of the script, and once you save, the file/script is created.

---

### Post by wickedcultgod on 2009-03-06
You guys rock! Thank you so much. The Ubuntu community rules. So, in essence, what I needed to  do was use gksudo before gedit to create the file? It works I just want to educate myself on why it works.

---

### Post by Kinney on 2009-03-06
It works because gksudo(or sudo for CLI) runs the editor as a superuser otherwise you wouldn't be able to save to that directory without the appropriate permissions.

If you run the following command you'll notice that the file is owned by the user "root".
```
ls -l /etc/pm/sleep.d/
```

If you try saving a file to that directory without running the editor with gksudo it will fail because you don't have the appropriate permissions. If you then save the file to your home directory and run the above command on that directory you'll see the file is owned by your user account. Hope this helps to explain it.

---

