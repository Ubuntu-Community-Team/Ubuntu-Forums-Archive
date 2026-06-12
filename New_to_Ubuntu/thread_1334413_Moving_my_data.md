---
title: "Moving my data"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by bj218 on 2009-11-22
In detail how do I move my data ie bill to a separate partition?

---

### Post by Merk42 on 2009-11-22
Do you have said partition created?
If so it's just like moving data anywhere, drag n drop.

Unless your question is more complex, like how you would make a partition, or mount said partition as /home or something.

---

### Post by bj218 on 2009-11-22
> **Merk42 said:**
> Do you have said partition created?
If so it's just like moving data anywhere, drag n drop.

Unless your question is more complex, like how you would make a partition, or mount said partition as /home or something.

I put my new partition on the desktop ie %home ubuntu I then went to Computer-File Browser & clk on bill then i went to view & clk on Show
Hidden Files i then highlighted all the files ie Ctrl A then i dragged
them to %home ubuntu this returned  the following message ¨Error while copying the folder Desktop cannot be copied because you do not have
permissions to create in the destination¨

---

### Post by coffee on 2009-11-22
I think you need to open the new partition with sudo privileges.

```
sudo nautilus /%home
```

This should give you the ability to do what you want.

coffee

---

### Post by bj218 on 2009-11-22
> **coffee said:**
> I think you need to open the new partition with sudo privileges.

```
sudo nautilus /%home
```

This should give you the ability to do what you want.

coffee

Could you give me a little more detail on how to do this!!

---

### Post by coffee on 2009-11-22
> **bj218 said:**
> Could you give me a little more detail on how to do this!!

Open a terminal (Applications -> Accessories -> terminal) and enter the string stated above and the prompt and press enter.  You will be asked for your password, type it in (it will not be displayed) and press enter.  A Nautilus window will open with root permissions. You should then be able to copy you files over.

Another option I have is a Python backup script I have written you could use.  Create a directory in you home dir called *bin* and then you can download and extract this *.tar.gz file to ~/bin/ and follow the README inclosed to get it setup and then run the script by typing the folowng:

```
cd ~/bin/savethehouse/src
      python sth.py
```

This should also do the trick, if you get a permission error type:
```
sudo python sth.py
```

If you try *savethehouse* let me know if it worked for you.

[[COLOR="Red"]savethhouse[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=137189&d=1258907564")

coffee

---

### Post by coffee on 2009-11-22
Another option to move you home files to another partition can be found [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

The Ubuntu documentation about Partitioning and Moving Home

---

### Post by coffee on 2009-11-25
Have you been able to get the move done?

Just thought I would check in and see how things are going.

coffee

---

