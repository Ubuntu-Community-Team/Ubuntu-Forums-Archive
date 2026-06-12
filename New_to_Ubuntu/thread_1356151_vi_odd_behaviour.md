---
title: "vi odd behaviour?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by rebeltaz on 2009-12-15
I am used to using vim on my OpenWrt router, but vim isn;t installed by default under Ubuntu, so I have been trying to use vi. Every time I try to use the arrow keys or the backspace button in insert mode, rather than performing the expected action, there is instead characters printed on the screen. Is this something that I am doing wrong? Is there a way around this, other than installing vim? 

Thanks...

---

### Post by chillicampari on 2009-12-15
There's a few ways to go about fixing it:

[http://www.ibb.net/~anne/keyboard.html]("http://www.ibb.net/%7Eanne/keyboard.html")

but it might just be easier to install vim:

```
sudo apt-get install vim
```

---

### Post by rebeltaz on 2009-12-16
> **chillicampari said:**
> There's a few ways to go about fixing it:

[http://www.ibb.net/~anne/keyboard.html]("http://www.ibb.net/%7Eanne/keyboard.html")

but it might just be easier to install vim:

```
sudo apt-get install vim
```

Wow, you ain't kiddin'. That is a little involved! I actually already did install vim, since that's what I was used to anyway, but I wasn't expecting a 27 meg program for (what I thought was) a (relatively) simple text-based editor!

---

### Post by chillicampari on 2009-12-16
And my spouse just chimed in talking about some one liner fix, but can't remember the syntax (and apparently it breaks something else). 

I think the page talks about almost every possible setup and envionment, *maybe* just the bash shell config and and an .Xresources could do the trick, I should probably try that to see if I end up using plain vi so I know in the future. 

27mb? I don't remember it being that large, yikes!

---

### Post by xifer on 2009-12-16
> **chillicampari said:**
> And my spouse just chimed in talking about some one liner fix, but can't remember the syntax (and apparently it breaks something else). 

I think the page talks about almost every possible setup and envionment, *maybe* just the bash shell config and and an .Xresources could do the trick, I should probably try that to see if I end up using plain vi so I know in the future. 

27mb? I don't remember it being that large, yikes!

There is always the option of learning to use vi
I use vim but rarely use the arrow keys and backspace key. 
Just press escape to exit from edit mode and then h is back, j is down, l is forward and k is up.  x to delete a char, dd to delete a line etc etc
i to insert, a to append, o to open a new line below

Honest guv, it works well when you get used to it

---

### Post by chillicampari on 2009-12-16
Actually, I used vi before vim was around, but now I'm old and grumpy and sort of enjoy having the backspace and arrow keys behavinn^Hg like most everything else. :P

---

### Post by llawwehttam on 2009-12-16
Hmm I used to use vi and vim all the time but now in starting to use gedit much more in graphical mode. nano works too though if you want something lightweight and simple. I think it comes installed as default.

---

### Post by cholericfun on 2009-12-16
in the .vimrc try adding

```
syntax on
```

that *might* do it although not sure if thats vim already...

---

### Post by rebeltaz on 2009-12-16
> **xifer said:**
> There is always the option of learning to use vi
I use vim but rarely use the arrow keys and backspace key. 
Just press escape to exit from edit mode and then h is back, j is down, l is forward and k is up.  x to delete a char, dd to delete a line etc etc
i to insert, a to append, o to open a new line below

Honest guv, it works well when you get used to it

I don't know that I _could_ get used to that! :confused: I mean, there isn't even any correlation in their layout to their commands. I might could understand, and get used to, say H is left, J is right, U is up and N is down - at least their position on the keyboard gives an indication of what they should do. Or if U is up, D is down, R is right and L is left - well, duh. In the scheme you mentioned it seems like they just had a few letters left laying around and said, 'hmmm, what can we do with these?'

No wonder I was having trouble with vi!

> **llawwehttam said:**
> Hmm I used to use vi and vim all the time but now in starting to use gedit much more in graphical mode. nano works too though if you want something lightweight and simple. I think it comes installed as default.

Even though I run the X graphical environment, it still reminds me too much of WindoZe. I like to do as much as I can in terminal mode, if only to help me remember the days when everything I did on a computer had to be done from a DOS command line. I may not fully understand everything about Linux yet, but hopefully I can learn enough to be at least as proficient in at as I once was with DOS. In that area I was a whiz, but that was many years ago. Do people still even know what DOS is, much less what it stands for (or even that it _is_ an acronym and not a word)? I digress.... 

> **cholericfun said:**
> in the .vimrc try adding

```
syntax on
```

that *might* do it although not sure if thats vim already...

I thank that is vim...

---

### Post by cholericfun on 2009-12-16
in reply to my post:

> **rebeltaz said:**
> 

I thank that is vim...

maybe, but i forgot to mention that this was the magic way i got rid of this behaviour of not beeing able to use arrow keys and such, whether it was vi or vim.

---

### Post by rebeltaz on 2009-12-17
> **cholericfun said:**
> in reply to my post:



maybe, but i forgot to mention that this was the magic way i got rid of this behaviour of not beeing able to use arrow keys and such, whether it was vi or vim.

Hmmm... even after installing vim, I did a search for .vimrc on the entire filesystem and didn't find it. What directory is that file in?

---

### Post by benj1 on 2009-12-17
> **rebeltaz said:**
> Wow, you ain't kiddin'. That is a little involved! I actually already did install vim, since that's what I was used to anyway, but I wasn't expecting a 27 meg program for (what I thought was) a (relatively) simple text-based editor!

i know, people take the piss out of emacs but vim is very nearly as big

anyway, vim tiny is installed by default, wouldn't that have the same functionality as vi

---

### Post by RedSquirrel on 2009-12-17
> **rebeltaz said:**
> Hmmm... even after installing vim, I did a search for .vimrc on the entire filesystem and didn't find it. What directory is that file in?
You can create the **.vimrc** file under your home directory. If you like, you can start with the one at /etc/vim/vimrc.

```
cp /etc/vim/vimrc ~/.vimrc
```

---

### Post by mvalviar on 2009-12-17
try
```

set nocompatible
syntax on

```

---

### Post by rebeltaz on 2009-12-17
OK... I copied /etc/vim/vimrc to ~/.vimrc and syntax was already set to on. I ran vi and it worked as expected. So I uninstalled vim and vim-runtime (which I noticed was the 27 meg part - vim itself was only like 2 kb) and tried vi again. It still works as expected. So I guess that file did the trick. Thank you.

---

