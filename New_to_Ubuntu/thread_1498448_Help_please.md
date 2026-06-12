---
title: "Help please"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by G1z3r on 2010-05-31
I am trying to do what is mentioned in the post below but i have no clue what I am doing can someone please help. I have downloaded the file but dont know where to go from there.

                                  **"Ubuntu 9.10 Ideazon Merc zboard gaming keyboard**             
                                                                I have read  over several articles on here and the web on how to get an Ideazon Merc zboard  gaming keyboard to work. I have tried various 'solutions' that never  worked. I did however pick up on all the knowledge that was passed  around and decided I would try something on my own.

What I did, was open gEdit and create a file to load the missing keymaps  for the gaming keys on the keyboard. I did this, because all of the  other keys work just fine (including the multimedia keys) right out of  the box on a fresh install of Ubuntu 9.10. I will attach the file so  that others might use it as well. What I would like to do however, is to  have it load automatically on startup of the Xsession. If anyone knows  how to do this, please reply to this post. Thanks in advance.

Edit: I have found how to do this by adding it to the Startup  Applications. Now, it is enabled every time I log in. Life and gaming in  linux just keep getting better and better. :smile:

As far as the file, save it to your home directory and run it with the  command: sudo ./zboard.sh
This will load the missing keymaps for the gaming keys on the left side  of the keyboard.

If this has helped you, I am glad that I could contribute back to the  community that has done so much for me.

Thanks,
:grin:
                                                                                                                                                        Attached Files                                               [IMG]http://ubuntuforums.org/images/attach/sh.gif[/IMG]     [zboard.sh]("http://ubuntuforums.org/attachment.php?attachmentid=144919&d=1264416723")  (1.1 KB, 25 views)"

---

### Post by nhasian on 2010-05-31
please use more descriptive titles so people can help you better.  also please mark the thread solved.

---

### Post by nhasian on 2010-06-01
i don't think you specified where your trouble was, so lets start from the beginning.  open up a terminal from Applications-> accessories-> terminal

change directory to wherever you put the file zboard.sh

make it executable with the command:

```
chmod +x zboard.sh
```

then execute the script:

```
./zboard.sh
```

good luck!

---

### Post by G1z3r on 2010-06-01
with some help from my wife, ok a lot of help with my wife we got it figured out. thank you so much for the help. sorry for the confusion.

---

### Post by nhasian on 2010-06-01
great!  what did you have to do to get it working?  in case someone else has the same issue...

also please mark the thread solved.

> **G1z3r said:**
> with some help from my wife, ok a lot of help with my wife we got it figured out. thank you so much for the help. sorry for the confusion.

---

