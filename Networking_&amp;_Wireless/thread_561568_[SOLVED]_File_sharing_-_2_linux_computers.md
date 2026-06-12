---
title: "[SOLVED] File sharing - 2 linux computers"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by tekkenlord on 2007-09-27
Hello friends. My setup is the following:

Internet -> router -> {kubuntu_box(1), kubuntu_box(2), windows_box}

I have kubuntu_box(1) and I want to be able to easily (and safely) access a directory in kubuntu_box(2) and vice versa (I do not care about the windows box). Can anyone suggest any way to do that? I have heard about samba and nfs but have no idea on how to use them. So please...be gentle, I am a newbie in these things.

Thanks in advance.

---

### Post by gardener on 2007-09-27
Do you need to transparently integrate it as a mounted drive or folder? If not, perhaps SCP? 

Start here [http://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by tekkenlord on 2007-09-27
Thanks for the help. I tried using fish from konqueror and it works but only one way, eg kubuntu_box(2) can connect to my kubuntu_box{1} but I cannot connect to kubuntu_box(2). When I try to connect to box(2) konqueror prompts me for the password, I give the correct password but it keeps asking for it. The same procedure from box(2) to box(1) is successful. Can you please help me a bit more?

EDIT: Never mind, I was using the wrong username.

---

