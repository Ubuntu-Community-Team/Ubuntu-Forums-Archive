---
title: "Stuck with vim-tiny"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by kgroll on 2010-02-12
I recently installed Ubuntu 9.10, which - if I understand correctly - includes vim-tiny, rather than the full version of this editor.

I only realized this after creating a .vimrc file in my home directory.  After creating this file and trying to open vim in my terminal, I receive:

```
kgroll@dp:~$ vim temp.txt
Vim: Caught deadly signal ABRT
Vim: Finished.

Vim: Double signal, exiting
Segmentation fault
```

I thought I might have specified something wrong in my .vimrc, so I stripped everything out except: ```
syntax on
```

Still no luck. After a little reading, I realized that I was using vim-tiny, which doesn't support the vim configuration file. So, I downloaded and compiled the latest source, thinking that would fix my problem.  Still no luck! 

Next I figured there might be a conflict, so I tried to remove vim with the following commands:
```
sudo aptitude remove vim
sudo aptitude remove vim-tiny
sudo aptitude remove vim-runtime
sudo aptitude remove vim-common
make clean (from where I compiled the source)
make distclean (from where I compiled the source)

```
I followed this with:
```
sudo apt-get install vim
```
I restarted just for good measure, and once again tried to start vim using my .vimrc file containing only 'syntax on'
Still receives the abort signal!

Vim-tiny is hardly usable, but I can't seem to replace it with a full install. Can anybody point me in the right direction here?

Much thanks

---

### Post by Dougie187 on 2010-02-12
I don't really think your problem is with vim-tiny. Because I'm using it, and it works great for me.

To start. have you tried moving your .vimrc so you don't use it? also, what version of vim are you using? (vim --version) should do it.

---

### Post by kgroll on 2010-02-12
Thanks for the prompt response.

You make a good point - I cannot confirm that using vim-tiny is really the root of my problem.

However, I CAN confirm that the .vimrc file IS my problem.  Check out the following sequence of commands (with my comments added as //):
```

kgroll@dp:~$ rm .vimrc
kgroll@dp:~$ vim temp.txt //vim loads fine if no .vimrc file is present
kgroll@dp:~$ vim .vimrc   //Create new .vimrc, containing only 'syntax on'
kgroll@dp:~$ vim temp.txt //Try to edit text doc now that .vimrc has been created
Vim: Caught deadly signal ABRT
Vim: Finished.

Vim: Double signal, exiting
Segmentation fault
kgroll@dp:~$
```

This clearly illustrates that if a .vimrc file exists in my home directory, vim will NOT start.

```
kgroll@dp:~$ vim --version
VIM - Vi IMproved 7.2 (2008 Aug 9, compiled Feb 12 2010 09:11:35)
Compiled by kgroll@dp
Normal version without GUI.  Features included (+) or not (-):
-arabic +autocmd -balloon_eval -browse +builtin_terms +byte_offset +cindent 
+clientserver +clipboard +cmdline_compl +cmdline_hist +cmdline_info +comments 
+cryptv -cscope +cursorshape +dialog_con +diff +digraphs -dnd -ebcdic 
-emacs_tags +eval +ex_extra +extra_search -farsi +file_in_path +find_in_path 
+float +folding -footer +fork() -gettext -hangul_input -iconv +insert_expand 
+jumplist -keymap -langmap +libcall +linebreak +lispindent +listcmds +localmap 
+menu +mksession +modify_fname +mouse -mouseshape -mouse_dec -mouse_gpm 
-mouse_jsbterm -mouse_netterm -mouse_sysmouse +mouse_xterm -multi_byte 
+multi_lang -mzscheme -netbeans_intg -osfiletype +path_extra -perl +postscript 
+printer -profile -python +quickfix +reltime -rightleft -ruby +scrollbind 
-signs +smartindent -sniff +statusline -sun_workshop +syntax +tag_binary 
+tag_old_static -tag_any_white -tcl +terminfo +termresponse +textobjects +title
 -toolbar +user_commands +vertsplit +virtualedit +visual +visualextra +viminfo 
+vreplace +wildignore +wildmenu +windows +writebackup +X11 -xfontset -xim 
+xsmp_interact +xterm_clipboard -xterm_save 
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
      user exrc file: "$HOME/.exrc"
  fall-back for $VIM: "/usr/local/share/vim"
Compilation: gcc -c -I. -Iproto -DHAVE_CONFIG_H     -g -O2        
Linking: gcc   -L/usr/local/lib -o vim    -lXt -lm -lncurses
```

---

### Post by Dougie187 on 2010-02-12
Well, we both have the same version.. And I am using a vimrc as well. If you want you can try using my vimrc, and see if it works for you.. here it is.

```
syntax on
set number
set tabstop=4
set shiftwidth=4
set modeline
set modelines=5

set ai
set ic
set hls 
"set lbr
"set foldmethod=marker
"set backup
" colorscheme zellner
set viminfo='10,\"100,:20,%,n~/.viminfo

" REQUIRED. This makes vim invoke Latex-Suite when you open a tex file.
filetype plugin on

" IMPORTANT: win32 users will need to have 'shellslash' set so that latex
" can be called correctly.
set shellslash

```

Note, a lot of the extra stuff is just from latexsuite. Let me know if it works or not.

---

### Post by kgroll on 2010-02-12
While I was trying to troubleshoot my problem originally, I decided to strip everything out of my vimrc file so that I was positive it wasn't the source of the problem.  I ended up with the following content in my .vimrc:

```
syntax on
```
That's it!  For this reason, I'm positive that there's nothing wrong with the content of the file. Rather, the fact that I'm trying to give a command (such as syntax on), is enough for vim to abort.

I can prove this by starting vim (after removing the .vimrc file), and then trying to issue
```
:syntax on
```
As soon as I press enter, vim exits.

This again leads me to believe that it is an issue with vim-tiny being run instead of the full version.  Could this be a path priority problem? As in, even though I've compiled the full version, it's still somehow executing the tiny version of vim?

I'm including a little more information below that may or may not help.
```
kgroll@dp:~$ which vim
/usr/local/bin/vim
```
```
kgroll@dp:~$ dpkg -l vim*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-=========================
ii  vim                      2:7.2.245-2ubuntu2       Vi IMproved - enhanced vi editor
ii  vim-common               2:7.2.245-2ubuntu2       Vi IMproved - Common files
un  vim-doc                  <none>                   (no description available)
un  vim-gnome                <none>                   (no description available)
un  vim-gtk                  <none>                   (no description available)
un  vim-lesstif              <none>                   (no description available)
un  vim-nox                  <none>                   (no description available)
ii  vim-runtime              2:7.2.245-2ubuntu2       Vi IMproved - Runtime files
un  vim-scripts              <none>                   (no description available)
rc  vim-tiny                 2:7.2.245-2ubuntu2       Vi IMproved - enhanced vi editor - compact version
```

PS: I need to run some errands for the next couple hours, so I'll have to check back later. Thanks again for your time and support.

---

### Post by Dougie187 on 2010-02-12
For some reason you are running vim from /usr/local/bin/vim which makes me think you are still using the version you compiled. I would try again with the /usr/bin/vim one. Then let me know what happens.

---

### Post by kgroll on 2010-02-12
Ah, you are absolutely correct. If I say 'vim temp.txt' then /usr/local/bin/vim is executed, and as a result, it aborts. However, if I say '/usr/bin/vim temp.txt' then the .vimrc file is accepted and works swimmingly.

I'd like to ask a couple more questions to solidify (or rather, establish) my understanding of what's happening here.

1. Does this mean I have two *unique* versions of vim installed? If I type vim --version, it must be querying the version of vim from /usr/local/bin/ (which returns VIM - Vi IMproved 7.2). 
1a. How can I identify the version executed at /usr/bin/ ?

2. If the /usr/local/bin/vim is the version I compiled this morning, does that installation directory get specified by ./configure by default because I didn't use the location prefix?
2a. Does that mean the /usr/bin/vim version exists because I used 'sudo apt-get install vim' ?

3. Finally, although I think I could just change the priority of those directories in my environment path, I'd rather just completely remove the version that doesn't work.  Any help on how I could do that?

Thank you

---

### Post by Dougie187 on 2010-02-12
> **kgroll said:**
> 1. Does this mean I have two *unique* versions of vim installed? If I type vim --version, it must be querying the version of vim from /usr/local/bin/ (which returns VIM - Vi IMproved 7.2). 
1a. How can I identify the version executed at /usr/bin/ ?

It appears that you would have two versions installed. One in /usr/bin and one in /usr/local/bin. I am going to assume that the /usr/local/bin one was installed through some compilation of code that you did. If you want to identify the version that exists in /usr/bin you would simply do what you did to run that version. In a terminal just type
```
/usr/bin/vim --version
```
and you should get what you are looking for.

> **kgroll said:**
> 2. If the /usr/local/bin/vim is the version I compiled this morning, does that installation directory get specified by ./configure by default because I didn't use the location prefix?
2a. Does that mean the /usr/bin/vim version exists because I used 'sudo apt-get install vim' ?

I would think that /usr/bin/vim was created when you did sudo apt-get install vim like you suggest, but the /usr/local/bin/vim version most likely got installed when you did
```
sudo make install
```
with the source code. I would suspect that this lingered because the command you said you ran was ```
make clean
make distclean
```
Where you should probably have ran something like
```
sudo make uninstall
sudo make distclean
```

I don't really think you need the clean ones, because those simply clean your workspace, removing compiled code so you can recompile everything, removing object files and what not.

> **kgroll said:**
> 3. Finally, although I think I could just change the priority of those directories in my environment path, I'd rather just completely remove the version that doesn't work.  Any help on how I could do that?

I think you could do what I said before, however if that doesn't work. Simply modify the PATH variable, to have /usr/bin before /usr/local/bin though, that is not typically ideal, because you would usually install software to /usr/local/bin, and the assumption is you would rather run that software than the software installed in /usr/bin. Because you know what you are doing.

Anyways, let me know if you have anymore questions. Good luck!

---

### Post by kgroll on 2010-02-13
Thank you very much for helping me understand this issue Dougie187. The problem has now been resolved, and as a bonus, I now fully understand where I went wrong.

As the final step, to anyone following along now or in the future - I simply needed to 'make uninstall' to remove my compiled version of vim.  I had unfortunately removed the source folder after I thought I had uninstalled it the first time, but just downloaded the source again, created a new make file (./configure followed by sudo make), and then issued the make uninstall command.

Finally using vim again in it's full glory!

---

### Post by Dougie187 on 2010-02-14
Glad you got it worked out. That is one of the issues with compiling from source. The only two ways to remove the software are to go into all the directories and manually delete the installed files, or to do "make uninstall" from the source. But that means you have to keep the source around until you remove it. So when I install something from source, I usually just save the tar file somewhere so I have it if I want to uninstall it.

---

