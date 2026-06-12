---
title: "Problems with my ibus and chinese(traditional) input"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by ranian on 2010-07-19
Dear All,

I am using Ubuntu 10.04 on my laptop. Ubuntu works well until someday I found that I forget to set up my Chinese(traditional) input method. Since I live in Taiwan, and I have tried ibus with chewing (&#37239;&#38899;) in previous version of Ubuntu 9.x, so I tried to set it up in my 10.04. Then here comes the problems:

What I have done:

[LIST=1]
[*]I went to "language support", and installed Chinese traditional, with all the check boxes checked (input methods included).
[*]I went to "ibus preference", and tried to find chewing input method, but didn't find it.
[*]I wanted to check if chewing input method is installed, so I went to "software center" and search ibus in my "installed software". It turned out that chewing input engine was installed.
[*]I guessed that chewing engine was not registered in some kind of ibus config file, but I am such a rookie and not sure about how to deal with this, so I decided to remove ibus by removing everything related with ibus I can find in my installed software.
[*]I looked up in some Taiwan forums and blogs, and found that maybe I can installed ibus with chewing by typing "sudo aptitude install ibus-chewing", and it worked!
[/LIST]
Now I can find chewing in my "ibus preference" and use it.
However....

[LIST=1]
[*]Since then, every time I goes to "language support", "language support" shows some loading message, and it's window disappears, just like nothing had happened. I can not access "language support" any more!
[*]Whenever I look up "ibus" in my "software center", the window of "software center" also disappears! "ibus" becomes a deadly key word in my "software center"!
[/LIST]
It is quite frustrating because some of my folders and applications are named in Chinese while some of them are named in English. I guess there is something wrong with my modification to ibus, but I have no idea about how to solve it. 

Please help me :confused:

---

