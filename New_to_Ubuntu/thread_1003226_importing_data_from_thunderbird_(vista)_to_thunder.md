---
title: "importing data from thunderbird (vista) to thunderbird in ubuntu"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by eskararriba on 2008-12-05
hi, 

I m busy importing my data from thunderbird on vista to thunderbird on ubuntu 8.10 - I followed all the steps indicated in this thread: 
[http://ubuntuforums.org/showthread.php?t=248631](http://ubuntuforums.org/showthread.php?t=248631)

nevertheless, thunderbird doesn t display mi accounts or messages. in the mozilla.thunderbird-folder, there are 2 "XXX.default" folders, the one I put there and another one (which is there by default, I guess).

any ideas?
thanks!

---

### Post by 73ckn797 on 2008-12-05
Go to the Thunderbird "profiles.ini" and change the path to the profile directory you copied to Ubuntu from Vista. You also can copy the contents from the xxx.default directory of Vista into the default xxx.default directory in Ubuntu. It seems that you have copied the entire xxx.default directory from one to the other and that is why you have 2 of them. The one created for the Tbird installation only will need the contents from the other one. Not the directory xxx.default completely.
+
Here is an earlier post of how I have done it. Works everytime.

[http://ubuntuforums.org/showthread.php?t=969448](http://ubuntuforums.org/showthread.php?t=969448)

---

### Post by eskararriba on 2008-12-06
thanks, it worked perfectly!

---

### Post by ace007 on 2008-12-06
for future reference you can use 

```

thunderbird --profilemanager

```

And then you can manage where thunderbird thinks your profile is.  For instance you could point thunderbird in Ubuntu to use the same profile folder Vista does, on the Vista partition.  Now you have one profile folder instead of two to manage.


cheers

---

