---
title: "cannot enter password"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by stef-l on 2010-10-26
Have just tried for the nth time to upgrade from 8.04 to 10.04.  As always, it has failed to boot up once installed.

Put in 10.04 dsc & asked it to repair a broken system.  It seems to have done so,but has presented me with a login screen.

It asks for my login & I can type this is & t shows.
Then it asks for my password, but nothing can be entered; the cursor stays where it is, does not move, so no password is entered & I can't get into ubuntu (if it's there) I'm using the only password I ever used for ubuntu.

Any suggestions?

Thanks

---

### Post by lavinog on 2010-10-26
Try pressing CTRL-ALT-F1 and test to see if you can login with text mode.

If you can login into text mode, try updating the system...there might be a broken package somewhere from the update.
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by mcduck on 2010-10-26
> **stef-l said:**
> Have just tried for the nth time to upgrade from 8.04 to 10.04.  As always, it has failed to boot up once installed.

Put in 10.04 dsc & asked it to repair a broken system.  It seems to have done so,but has presented me with a login screen.

It asks for my login & I can type this is & t shows.
Then it asks for my password, but nothing can be entered; the cursor stays where it is, does not move, so no password is entered & I can't get into ubuntu (if it's there) I'm using the only password I ever used for ubuntu.

Any suggestions?

Thanks
If you are trying to log in at command line, keep in mind that when you type your password nothing is printed on screen. Just type the password and press enter, and it *will* work. :)

---

