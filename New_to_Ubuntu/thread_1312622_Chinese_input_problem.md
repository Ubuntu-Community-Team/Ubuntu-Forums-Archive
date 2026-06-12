---
title: "Chinese input problem"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by chiewcy on 2009-11-03
Greetings, I am new in using ubuntu, i installed ubuntu 9.04 recently and updated to ubuntu 9.10, i tried to add chinese input for my computer and i manage to make it show something like the screen shot, but still i not able to type chinese word, is there anything i need to do to complete it?

---

### Post by chiewcy on 2009-11-03
I manage to solve the problem already, i type the command 

$sudo apt-get install scim-qtimm im-switch scim-pinyin
$im-switch -z en_US -s scim

Although i not so sure what happened, but seems this is the last step have to do to enable chinese input. Anyway, sorry for posting this noob question, thanks.

---

### Post by webguru on 2009-11-29
I believe the 9.10 is using ibus input method now. Check the blog post for the complete Chinese input method in 9.10 instruction.

[http://lichao.net/eblog/how-to-input-chinese-cjk-in-english-ubuntu-9-10-200911429.html](http://lichao.net/eblog/how-to-input-chinese-cjk-in-english-ubuntu-9-10-200911429.html)

---

