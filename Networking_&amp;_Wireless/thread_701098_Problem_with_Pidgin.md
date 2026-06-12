---
title: "Problem with Pidgin"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by thelugnut on 2008-02-19
I have a problem with Pidgin. 

I selected "Add Buddy Pounce", ...
...Pounce when Buddy Signs on...
...Starts Typing...
...Stops typing...

and under Action
...Pop up notification...

I quickly discovered these were horrible choices and tried to undo them.

Nothing I do stops these messages from popping up.

I even uninstalled the app, and then reinstalled it.

Nothing helps. I am on the verge of removing it and using something else.

Can anyone help me here?

Many thanks.

---

### Post by agim on 2008-02-19
Uninstall the application. Remove the file .purple from your home directory. Reinstall. Should do the trick.
The .purple file is the pidgin config file.

---

### Post by thelugnut on 2008-02-19
Worked good, lasts a long time.

Many thanks...

---

### Post by features on 2008-02-19
Close Pidgin, then you can manually edit the pounces.xml file:

```

gedit ~/.purple/pounces.xml

```

You want to make it look like this...

```

<?xml version='1.0' encoding='UTF-8' ?>

<pounces version='1.0'/>

```

Alternatively you can, in Pidigin, go to Tools-->Buddy Pounces, select the pounce, then click the "Delete" button.  The pounce won't be deleted until you restart Pidgin tho...

---

