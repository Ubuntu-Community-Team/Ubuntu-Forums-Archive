---
title: "Vim modes"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-17
I'm trying to get the hang of using the vim text editor, but one thing is making it more difficult than it should be. From what my textbook tells me, it's supposed to say what mode I'm in on the bottom of the display (I'm working in bash), but it doesn't. So if I hit the "insert" button, I *may* be in insert mode, but it doesn't tell me anywhere that I am. And if I toggle through the modes, *fuggedaboudit*, I have know idea what mode I'm in. Could the fact that I'm using Lucid Desktop on a netbook have something to do with it?

---

### Post by Chris1274 on 2010-07-17
Never mind. "i" gets it into insert mode, not "insert" as the book says.

---

### Post by kellemes on 2010-07-17
Couple of links that may help..
[http://www.linuxconfig.org/Vim_Tutorial]("http://www.linuxconfig.org/Vim_Tutorial")
[http://jmcpherson.org/editing.html]("http://jmcpherson.org/editing.html")

---

### Post by Chris1274 on 2010-07-17
Thanks! I came across this one as well:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAdvanced_vi.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdvanced_vi.html)

---

### Post by capscrew on 2010-07-17
> **Chris1274 said:**
> I'm trying to get the hang of using the vim text editor, but one thing is making it more difficult than it should be. From what my textbook tells me, it's supposed to say what mode I'm in on the bottom of the display (I'm working in bash), but it doesn't. 
My favorite editor.  You are not working in bash.  Bash is the command line shell.  Vim is the editor (app) the you invoke with the incantation ```
vi <name-of-file-you-are-editing>
``` If you are creating a new file you can just start vim without declaring the filename.  When you save it.
> 

So if I hit the "insert" button, I *may* be in insert mode, but it doesn't tell me anywhere that I am. 
As far as I know there is no "insert" button.  The key on your keyboard toggles the ***overwrite/insert ***a character condition when typing.> 

And if I toggle through the modes, *fuggedaboudit*, I have know idea what mode I'm in. Could the fact that I'm using Lucid Desktop on a netbook have something to do with it?

No, I use it on a laptop and desktop as well as CLI only servers.  There are actually 2 versions of VIM.  There is VIM and there is GVim.  Which are you using?

I am not at a machine that has VIM installed so this is by memory -- When you are in VIM (and I believe also in GVim) you can toggle through the modes this way:
```

**View Text**
  This is the default mode. When VIM is  started you are 
  in this mode.  Nnothing shown at the bottom and you can't
  alter the text.
  -- To return to this mode from other modes hit the ESC key

**Insert Mode** 
  Mode to edit text.  To enter this mode, hit the "i" key.
  It should now show "--insert" at the lower left.

**Save and/or Exit**
  You need to be in the View mode before you can enter the this
  mode.  From the View mode hit SHIFT-: key.  You should see a 
  **":"**character at the lower left.  At this point you can
  save your work or quit without saving. 

  Before you can get to the save mode you have to be in the view 
  mode -- you need to hit the ESC key and see that --Insert goes 
  away 
```

For some basic information see [_here_]("http://newbiedoc.sourceforge.net/text_editing/vim.html.en").

---

### Post by gmargo on 2010-07-17
Welcome to Vim.  As a new user, the most important thing to do first is to create a personalized **$HOME/.vimrc** file.  The very first option you should set in this file is "nocompatible" so that VIM acts like VIM and not like VI.  And that includes immediately enabling the "showmode" option which is the one you are looking for - to keep an mode-type indication on the screen.

So if you don't already have a **$HOME/.vimrc** file, here is your very first one:
```

" See ':help option-list' for short explanation of each option
 set nocompatible        " Use VIM features.

```Create that file, and restart VIM, and now hit the 'i' key - you should now see an "--INSERT--" flag at the bottom of the screen.

Now you can further customize your VIM options by editing this file.

---

### Post by Chris1274 on 2010-07-18
> **gmargo said:**
>  So if you don't already have a **$HOME/.vimrc** file, here is your very first one:
```

&quot; See ':help option-list' for short explanation of each option
 set nocompatible        &quot; Use VIM features.

```Create that file, and restart VIM, and now hit the 'i' key - you should now see an &quot;--INSERT--&quot; flag at the bottom of the screen.

Now you can further customize your VIM options by editing this file.

Can you explain that code to me (e.g., why are the quotes placed as they are? why is there a big space?) I just want to understand things before I implement them.

---

### Post by gmargo on 2010-07-18
The double quote starts a comment.  The "big space" is for alignment; my .vimrc has lots of other stuff, this is just the first two lines. The leading space on the "set" line is there so I can comment out a line with further indentation.

The vim distribution (BTW, you should install the **vim-gnome** package) includes examples, such as the files /etc/vim/vimrc and /usr/share/vim/vim72/vimrc_example.vim.

You can read the embedded documentation on the 'compatible' option by typing :help 'compatible'

---

### Post by Chris1274 on 2010-07-18
Done. Thanks very much for the help :)

---

