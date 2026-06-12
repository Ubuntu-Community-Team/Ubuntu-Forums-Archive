---
title: "HowTo execute command within gnome-terminal from shellscript"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by LarryJ2 on 2009-04-15
If I have a bash shell script "test.sh" with contents shown below   with 755 permissions which is visible on my desktop. So  why doesn't a double click on it's icon,  open a gnome-terminal session  with the title of "title" showing  and then execute the shell command "echo Hello" in that terminal window, which I thought should produce "Hello".

```
#!/bin/bash
echo "Hello"
gnome-terminal  -t  "title" -e echo Hello
```FYI:
> lj@lian:~/Desktop$ ls -al test.sh
-rwxr-xr-x 1 lj lj 68 2009-04-15 09:26 test.sh> lj@lian:~/Desktop$ cat test.sh
#!/bin/bash
echo "Hello"
gnome-terminal  -t  "title" -e echo HelloI was expecting a window to open, and see the "Hello" after all if I start gnome-terminal, enter "echo "Hello"  I  get "Hello" in the terminal

> lj@lian:~/Desktop$ echo Hello
Hello
What am I missing?  Thanks, Larry

---

### Post by ibuclaw on 2009-04-15
What you are missing?

The terminal window is opening and closing too quick for you to notice. ;)

Try something more permanent.

```

#!/bin/bash
echo "Hello"
gnome-terminal  -t  "title" -e 'touch Hello'

```

Then type in:
```
ls
```
and you should see a brand new file.

Regards
Iain

---

### Post by ibuclaw on 2009-04-15
> Last edited by LarryJ2; 1 Minute Ago at 04:40 PM.. Reason: Tried to add Tags... 

Scroll down below this post I have made, you'll see the words [COLOR="Red"]Quick Reply[/COLOR]. Now, look at the bar immediately above it named **Tags** and follow it to the right hand side of the firefox browser. You should now see a hotlink named **Edit Tags**. Click it, and add the tags you wish to attach to this thread. :)

Regards
Iain

---

### Post by LarryJ2 on 2009-04-15
Thanks Lian.  Yes,  if after double-clicking, if  I respond to the dialog box by selecting "Run in Terminal", I briefly see a gnome-terminal flash upon my screen.   Yes, I would like it to stay!! 

But how to  I 

1. invoke gnome-terminal from a shell script
2. have the gnome-terminal window open and then
3. have a command from within my shell script executed in  that gnome-terminal?

I understand what touch does.  As far as I can tell, that doesn't make my gnome-terminal stay on the screen.

---

### Post by iponeverything on 2009-04-15
you could add a:

```
sleep 5 

```
to the end

---

### Post by LarryJ2 on 2009-04-15
OK understand sleep 5  but I would like the terminal window to appear and stay up  until I click the close X button so I can monitor the results of my executing program.  The echo command is just a place holder for another program which dumps info messages and error messages to std.out.  

  Is there a sleep forever command?  (BTW, nice Cat avatar!)

More explanation, hopefully not confusing... if my script contains only  the lines
> #!/bin/bash
gnome-terminal

gnome-terminal obediently opens and stays up.

How do I pass a program with arguments into gnome-terminal so that the program is executed by the bash shell within gnome-terminal so I can monitor what it kicks back.

Larry

---

### Post by LarryJ2 on 2009-04-15
I guess I was asking the wrong question.
```
#!/bin/bash
MyExecutable     MyArguments
```
seems to work!  I guess any bash script that you ask to be run in a terminal automatically is run in gnome-terminal  if you are using the gnome desktop (or something like that!)

Anyway,  thanks the responses.

---

### Post by hovzio on 2009-04-15
> **LarryJ2 said:**
> I guess I was asking the wrong question.
```
#!/bin/bash
MyExecutable     MyArguments
```
seems to work!  I guess any bash script that you ask to be run in a terminal automatically is run in gnome-terminal  if you are using the gnome desktop (or something like that!)

Anyway,  thanks the responses.

Sure if you call a script, it is run as a child process to your current shell. Actually your script is being run by bash, gnome terminal is just a terminal emulator, there are many of these, xterm etc.. You can also specify a default emulator in gnome. Your actual shell is bash, which you are calling with the "shabang" (#!/bin/bash), the first line in your script. There are also many diff shells, korn shell, tcsh, sh the list goes on. ;)

---

### Post by LarryJ2 on 2009-04-15
> You can also specify a default emulator in gnome.
Sure enough, my  System->Preferences->Prefered Applications->System shows GNOME Terminal which is executed as  "gnome-terminal -x".

It still bothers me that gnome-terminal --help  shows 
>  -x, --execute  Execute the remainder of the command line inside the terminal.
so I would naively try (inside my  script)
> gnome-terminal -x echo "hello"
which I would interpret as "execute the gnome-terminal program and then inside the gnome-terminal window run the shell command echo "hello".  

But I never see a window with a shell prompt! Clearly, my interpretation is wrong.

---

