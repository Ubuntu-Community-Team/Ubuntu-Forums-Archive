---
title: "vimtutorial lesson 7.2"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by btf18 on 2011-03-17
Hi all, trying to complete the vimtutor lesson 7.2

Firstly, I may have done it, so can someone tell me how i open up the file "vimrc" and view it, to see if i did manage to write the vimrcEXAMPLE to my vimrc file. I need to check if it worked before i tell you my problems. Thanks :D

---

### Post by btf18 on 2011-03-17
I managed to open vimrc file and it didnt work. Im basically trying to copy text to my vimrc file from another file opened inside vim. so copy text from vim, into my vimrc. I press v and scroll to select the text, then i press :w vimrc.

Now this should work, but instead it comes up with a quick message: file already exists, press ! to override it. and the text doesnt get copied. What should i try? Pressing! in the directory name or somehwere else?

---

### Post by cong06 on 2011-03-17
alright. I'm a bit confused, but let's see:

I have two files: ~/.vimrc and ~/vimexample

I want to copy some text from ~/vimexample to ~/.vimrc

1) 'vim ~/.vimrc'
2) ':vs ~/vimexample'
3) '^v' select the text
4) '^w^w' to switch back to ~/.vimrc
5) 'p' to paste the text where you wanted
6) ':xa' to close and save all

Does that do it?
(text in quotes is the command, the "^" sign symbolizes the control key)
Note: if you accidentally enter "insert" mode, press escape a few times to leave. you shouldn't need to be in insert mode for this operation at all.

edit: silly smilies confusing my code...

---

### Post by btf18 on 2011-03-17
okay everything seems to work the first time but because its the first time i do it wrong and then after that i try again and it doesnt work. Your first command vim ~/.vimrc did work when i typed it into the terminal and opened the file. Now it wont see: ben@ubuntu:~$ vim ~/.vimrc
Error detected while processing /home/ben/.vimrc:
line    1:
E492: Not an editor command: item.
Press ENTER or type command to continue

But i believe your way will work if i can get that first command to work again. The only thing wrong with it is the vimrcEXAMPLE file is actually called: $VIMRUNTIME/vimrc_example.vim, but i did exactly what you did and called it vimexample which was my bad. Can you please tell me how to get to the part the first command takes me to so i can continue with the correct filename in place this time?

---

### Post by btf18 on 2011-03-17
Also your way is different to the vimtutor way. It seems a bit more complicated. If you want you can just type vimtutor into the terminal and vimtutor will come up then scroll down to lesson 7.2 and see if i did it the correct way. I believe what i explained i did was correct and should have worked. But if the case is its just not working for some weird reason then i definitely have to do it your way and im interested in learning your way regardless, as it seems pretty good :-)

Thanks heaps!

---

### Post by cong06 on 2011-03-17
> **btf18 said:**
> okay everything seems to work the first time but because its the first time i do it wrong and then after that i try again and it doesnt work. Your first command vim ~/.vimrc did work when i typed it into the terminal and opened the file. Now it wont see: ben@ubuntu:~$ vim ~/.vimrc
Error detected while processing /home/ben/.vimrc:
line    1:
E492: Not an editor command: item.
Press ENTER or type command to continue

But i believe your way will work if i can get that first command to work again. The only thing wrong with it is the vimrcEXAMPLE file is actually called: $VIMRUNTIME/vimrc_example.vim, but i did exactly what you did and called it vimexample which was my bad. Can you please tell me how to get to the part the first command takes me to so i can continue with the correct filename in place this time?

I'm still rather confused, but it seems like your "/home/ben/.vimrc" file is somehow corrupt or doesn't have the proper syntax?

can you copy the output of this:
```

cat ~/.vimrc

```


oh! looking at lesson 7.2, they start assuming that vim is open. I started assuming that vim wasn't open.

Also, their way is rather simple... (:e, :r, etc.)
My way lets you be super selective which stuff you want to add. It looks like the ":r"  command just dumps text to your file. (Lesson 5.4)

I should probably go through the vimtutor... I know how to do what I want, but I probably go about it inefficiently.


Oh wow! I need to look through that example ~/.vimrc. I didn't know you could use a mouse with it!

---

### Post by btf18 on 2011-03-18
Lol it sounds like you are enjoying the tutor. The output of you command is just item. see here:[CODE]ben@ubuntu:~$ cat ~/.vimrc
item.
[CODE]

Please let me know what you think about why i cant open my vimrc file to edit it.

I just realised what to do to do it the vimtutor way aswell, if i can just get [CODE]:e ~/.vimrc[CODE] to open up vimrc to edit it like the tutor says to do, i will be able to write the $VIMRUNTIME/vimrc_example.vim to it like it says to do. Either of your way or the tutors way will work if i can open the file. It now said this when i tried the :e ~/.vimrc command:You can add all your preferred settings to this "vimrc" file.
E325: ATTENTION
Found a swap file by the name "~/.vimrc.swp"
          owned by: ben   dated: Thu Mar 17 18:57:09 2011
         file name: ~ben/.vimrc
          modified: YES
         user name: ben   host name: ubuntu
        process ID: 5777
While opening file "/home/ben/.vimrc"
             dated: Thu Mar 17 18:52:56 2011

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /home/ben/.vimrc"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/home/ben/.vimrc.swp"
    to avoid this message.

Swap file "~/.vimrc.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort: 

What do?

---

### Post by btf18 on 2011-03-18
bump

---

