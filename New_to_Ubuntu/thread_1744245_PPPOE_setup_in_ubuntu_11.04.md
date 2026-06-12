---
title: "PPPOE setup in ubuntu 11.04"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by AnupBharti on 2011-04-30
hey guys i am newbie to ubuntu and installed 11.04 on my system and i am not able to run the pppoe utility from comannd prompt...it gives me that utility is not installed ...so i downloaded the .tar format of that utility and extracted it and went to command prompt to run the command but its giving me the error as permission denied even though i am logged in as root ...i dont know why .please see the attachment for the details ..now i have following questions--

1)does ubuntu 11.04 comes with any PPPOE utility??
2)what should i do as i am getting permission denied error even though i have given permission to folder and logged in as root..

Please suggest me guys!!

---

### Post by sisco311 on 2011-05-04
> **AnupBharti said:**
> 
1)does ubuntu 11.04 comes with any PPPOE utility??


Yes, you can configure it under nm-connection-editor -> DSL tab

---

### Post by dineshs on 2011-05-05
Try
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

### Post by jtarin on 2011-05-05
> **AnupBharti said:**
> hey guys i am newbie to ubuntu and installed 11.04 on my system and i am not able to run the pppoe utility from comannd prompt...it gives me that utility is not installed ...so i downloaded the .tar format of that utility and extracted it and went to command prompt to run the command but its giving me the error as permission denied even though i am logged in as root ...i dont know why .please see the attachment for the details ..now i have following questions--

1)does ubuntu 11.04 comes with any PPPOE utility??
2)what should i do as i am getting permission denied error even though i have given permission to folder and logged in as root..

Please suggest me guys!![https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by realzippy on 2011-05-05
```
sudo pppoeconf
```

does not work?

---

