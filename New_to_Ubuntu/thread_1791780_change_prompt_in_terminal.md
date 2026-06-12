---
title: "change prompt in terminal"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by offra350 on 2011-06-27
Hi all,
My problem is pretty minor, I think.

The guy that set my computer up, left a prompt I don't like. 
"james@offra-200:~$"

Can I permanently change this to :
"offra@hp200:~$"

If so, how?

Thank you

---

### Post by Wim Sturkenboom on 2011-06-27
issue 'hostname' command to change it temporarily
```

wim@desktop-01:~$ sudo hostname abc
wim@desktop-01:~$ 

```

result of above action (start a new terminal)
```

wim@**[COLOR="Red"]abc[/COLOR]**:~$ hostname
abc
wim@**[COLOR="Red"]abc[/COLOR]**:~$ 

```

If that works, edit /etc/hostname to make the change last after a reboot
```

wim@abc:~$ cat /etc/hostname
desktop-01
wim@abc:~$ 

```
The file still reflects the original hostname.

PS
read 'man hostname'

---

### Post by JKyleOKC on 2011-06-27
The previous post will change the name of your computer, but you don't have to do that to just change the prompt. By default, Ubuntu sets the prompt to "username@hostname:directory$" but you can change it to anything you want by redefining environment variable PS1.

To see how it works, open a terminal window and type "PS1=what?" then hit enter. The prompt should change to "what?" immediately, and remain that way until you log out and back in, open another terminal window, or issue another command to change PS1.

To make the change permanent, you must edit the hidden ".bashrc" file in your home directory. I recommend that you experiment with the temporary changes until you are certain of what you want. The default setting tells you (1) what user id you are currently using and (2) what directory you are in, both of which are nice to know. You may lose this information when you set your own permanent prompt.

---

### Post by mikenev on 2011-06-27
You can customize the prompt to look however you want it to. Check [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

### Post by CaptainMark on 2011-06-27
is there a list of the shorthand used for this, im assuming \u is username likewise \h is hostname is there anything else that can be added

---

### Post by JKyleOKC on 2011-06-27
That link in post #4 above includes such a list.

---

### Post by offra350 on 2011-06-27
I do thank everybody for the answers...but ?

Wim Sturkenboom - I want to change from  
> ]james@offra-200
to
> offra@hp200

JKyleOKC - 
> To make the change permanent, you must edit the hidden ".bashrc" file in your home directory.
I am new here, and that sounds complicated. I did find the file, but what am I suppose to do with it?

mikenev - 
> Check [http://www.cyberciti.biz/tips/howto-...up-prompt.html]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html")
That was also too complicated for me.

I apologise for being so dense, but as I said this is new to me.  You guys are like at sentence structuring, and I am like at "A-B-C".  :(

---

### Post by CaptainMark on 2011-06-27
@jkyle thanks, i i was probably typing when this post came through :P

---

### Post by JKyleOKC on 2011-06-27
About 55 lines down in the file, there will be a line that looks like this:```
PS1='${debian_chroot:+($debian_chroot)}[COLOR="Red"]\u[/COLOR]@[COLOR="Lime"]\h[/COLOR]:\w\$ '
```I've added the two colors to identify the parts you'd need to change. Replace the two characters in red with "offra" (without the quotes) and the two in green with "hp200" to get what you want, I believe.

You can do this with gedit or any other text editor that you like. However before you make the change, open a terminal window and back up the file with this command:```
cp .bashrc bashrc_bak
```This will let you undo your changes if they don't work out, by typing```
cp bashrc_bak .bashrc
```in another terminal window. This simply copies the unmodified file to a safety location, and later copies it back if need be.

You may have to log out and back in for the change to take effect; the comments say that the file is not used for "login shells" but my experience is that changes here do seem to take effect at login time.

---

### Post by inameiname on 2011-06-28
It sounds like you've already found what you are looking for, but in case you haven't found a good command prompt that you like, check out my Ultimate Bashrc for more possibilities: [http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746](http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746) .

In lines 184-683 I have over 60 of them inside which you can use; some one tier, some two tier, and some three tier, as well as a chart for the various punctuation possible in creating your own. I only mention this as before I created this bashrc, I had lots of trouble figuring out how to tweak the command prompt to the one I want, and so I put this together to help make it easier for me and anybody interested. Maybe it can help you find your favorite one if you haven't already.

---

### Post by Wim Sturkenboom on 2011-06-28
> **offra350 said:**
> I do thank everybody for the answers...but ?

Wim Sturkenboom - I want to change from  

replace 'abc' by 'hp200'; my mistake thinking that that was obvious ;)

and the new 'offra' is usually the username (sorry that I missed that part); in this case you must hard code it in .bashrc

---

### Post by offra350 on 2011-06-28
Thanks so much for your explanation and patience.  I believe my "problem" is now solved.

Thanks everybody !!!

---

