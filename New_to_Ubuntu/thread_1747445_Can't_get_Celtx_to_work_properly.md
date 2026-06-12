---
title: "Can't get Celtx to work properly"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by ElHombreDelSaco on 2011-05-02
Hi. I installed Celtx normally, like in their instructions (the 2.9.1 version) and it seems to only be working if I open it from terminal and using sudo, which I'd rather not do. Is there any way for me to properly install it so it's available for all users but so that I don't need to open a terminal window for it?

Also, the launcher shortcut for it only works if I tell it to open from the terminal. I've searched the forums but found nothing really conclusive, at least for this version and for what I want to do. Can anyone help me?

Edit: sorry I didn't say, but this is on Ubuntu 10.04 LL

---

### Post by manfromthezoo on 2011-05-03
Hello!

This is an interesting one, I've never had any trouble getting Celtx to run under any Ubuntu release before. But, the first thing I would check - based purely on what you described - is the permissions on the Celtx binary and directory.

Try doing a long directory listing on not just the binary, but the celtx directory itself.

So, from a terminal, **cd** to where you have the celtx directory extracted and run **ls -l**

Check the permissions and ensure your user is allowed to read and execute the the contents of the celtx directory.

You could also try extracting a fresh celtx directory to your home folder. Then, from a terminal, open the permissions up wide on it with **chmod 777 nameofceltxdirectory**. Also make sure that the celtx binary is executable, from within the celtx directory, with **chmod +x celtx**.

---

