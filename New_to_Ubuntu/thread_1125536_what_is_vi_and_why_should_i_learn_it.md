---
title: "what is vi and why should i learn it?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by superplasmafist on 2009-04-14
ive read and seen stuff aboput its important to learn vi.

im new to linux and want to learn everything. is this a good place to start or should i learn other stuff first?

i know theres something else called emacsbut that vi is better.

thanks

---

### Post by Penguin Guy on 2009-04-14
No, forget vi for now, learn the basics first. It is a text editor, but until you know what you're doing; stick with the standard one (presumably gedit).

---

### Post by SunnyRabbiera on 2009-04-14
Right, vi is more for prgrammers and hardcore linuxers.
I never had a use for it and typically use Gedit.

---

### Post by Penguin Guy on 2009-04-14
> **SunnyRabbiera said:**
> hardcore linuxers :lolflag: Well put.

---

### Post by superplasmafist on 2009-04-14
but what does it do?

what should i learn before i learn vi?

---

### Post by LowSky on 2009-04-14
personal I hate Vi the command are annyoing to master, but that my opinion, if you need an editor while in termnial, Nano works really well and is more geared to people used to a GUI interface.

---

### Post by LowSky on 2009-04-14
> **superplasmafist said:**
> but what does it do?

what should i learn before i learn vi?

Vi is just a text editor, that all, it made for people who need to edit files on the fly and by keyboard only. Some enviroments it make perfect sense to use, while for most it does not.

Like I mention Nano is a replacement and works very simply and has decent instructions on screen while editing files.

first thing to learn in Linux is basic commands and what they do

[http://www.reallylinux.com/docs/basic.shtml](http://www.reallylinux.com/docs/basic.shtml)

---

### Post by durand on 2009-04-14
If you really want to learn vi, try vim instead. It's installed by default on ubuntu and comes with a pretty interesting tutorial.
```
vim
```
```
vimtutor
```

Not that there is much reason to learn vim when you're a linux newbie. It's great as a command line replacement to gedit and so on but it's not that much better.

---

### Post by skitching on 2009-04-14
PenguinGuy is right; vi is not the first thing to learn.

Vi is a text-editing program that is particularly useful for writing programs. It is also useful for editing system configuration files. But until you begin getting seriously into programming or complex linux administration, you don't need to know it.

For simple text editing jobs, Gnome provides "gedit" and KDE provides "kate"; these are easier to learn, and are typically listed as "text editor" in your desktop menubar. Of course for writing letters, etc a word-processor like OpenOffice is more appropriate.

And for system configuration, there are graphical admin tools for most tasks; just see the "administration" menu in the menubar.

---

### Post by ddrichardson on 2009-04-14
vi is just a text editor. There was a time when there weren't any text editors and then along came vi and nano. Ubuntu actually uses VIM (Vi IMproved).

I like vi but then have been using it for a long time, don't worry about the editor - worry about the contents of the files.

Anyhoo, hardcore linux users use cat > filename ;-)

---

### Post by leandromartinez98 on 2009-04-14
I disagree. You can start learning Vi, its not big deal, with a few commands you can do basic editing like in any other editor. It is the
most ubiquitous editor out there, that is, you will find it in any
linux/unix/MacOS machine, already installed. You may hate it at first,
but after some basic learning of its commands you will see that 
you can edit files much more efficiently with it than with gedit,
for example (I won't say that much more than with any other editor
to avoid flame wars here...). Just keep in mind this: 

[esc] u

This is the "undo" command. Any bizar thing that may happen can be 
undone with that. If you really want to "learn everything" and,
particuarly, if you are a touch-typist, go for it. If you are not
a touch-typist, I suggest putting that on your list.

---

### Post by ddrichardson on 2009-04-14
If we're going down that road then the command I'd remember is guit without saving changes: ```
:q!
```Its very easy to open a read only file and not realise how to get out of it.

---

### Post by skitching on 2009-04-14
> **superplasmafist said:**
> but what does it do?

what should i learn before i learn vi?

One good place to start is by downloading the free ubuntu guide here and working through it together with your new Ubuntu install:
   [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

Then it depends on your interests. You could learn how to use OpenOffice, or if graphics is more your thing, then try learning how to use Inkscape or GIMP. Or if you really want to get to grips with the operating system, then under the "System|Help" menu there are lots of interesting pages.

---

### Post by Penguin Guy on 2009-04-14
To OP: Tell us a little about yourself. Presumably you are not a programmer?

---

### Post by Paqman on 2009-04-14
Vi is just a text editor that uses keyboard shortcuts so that you can edit text without having to use a mouse. Programmers dig it because it's fast once you're familiar with it, but it's got a very steep learning curve because it's pretty ancient, so doesn't conform to the standards of modern desktops.

If you're not producing vast amounts of raw text there's not really any point to learning it.

---

### Post by superplasmafist on 2009-04-14
okay i think i leave it for now then.

thanks for all the answers

---

### Post by Elfy on 2009-04-14
> **ddrichardson said:**
> If we're going down that road then the command I'd remember is guit without saving changes: ```
:q!
```Its very easy to open a read only file and not realise how to get out of it.

It's even worse to get stuck editing sudoers and not know how to get out :(

I still don't know why I couldn't get out.

---

### Post by The Cog on 2009-04-15
I was advised to learn the basics of vi many years ago. It is a text-mode editor available on pretty-much every flavour of 'nix. As such, it doesn't need a GUI and can be used to rescue or try to fix things pretty-much anywhere. It still works, even on this new-fangled Linux stuff. I have never regretted learning the very few vi commands I know - just enough to get by on when things are going really badly.

---

### Post by LowSky on 2009-04-15
> **forestpixie said:**
> It's even worse to get stuck editing sudoers and not know how to get out :(

I still don't know why I couldn't get out.

Same thing happened to me when setting up an Arch Linux install

Was not fun

---

### Post by ibuclaw on 2009-04-15
As a general rule of thumb, if you are either:
A) A programmer, or
B) Want a quick easy tool to edit config files in /etc and ~/.*rc

Then vim is the right tool for the job.

```
sudo apt-get install vim
```

and edit the .vimrc file
```
vim ~/.vimrc
```
Press **i**
and put in:
```

" Colour Hightlighting
syntax on
" Auto Indent
filetype indent on
" Press F2 key so pasted text doesn't get ruined by auto indent
set pastetoggle=<F2>
set nocompatible

```

Press **Esc**
Type in
```
:wq
```
Then reopen the file with vim again and see the nice new colours :)

To close, as mentioned earlier
```
:q
```
Don't like working in CLI?
```
sudo apt-get install vim-gtk
```
and use **gvim** instead.

The only thing that takes a small getting used to is the different **modes** that come with vim.

To quote a page:
```

# The Biggie: Vi has modes, modern editors are modeless.
    * This relates to how an editor performs its two main functions: entering text and executing commands relating to the text.
    * Most modern editors and word processors are modeless, so that a user may enter text (e.g., typing "A") or a command (^S to save the file) at any time.
    * Vi has three modes:
          o Text insert mode
          o Keystroke command mode (vi mode)
          o Command line mode (ex mode) 

# Plus and Minus for modeless:

    * (+) Familiar.
    * (+) Easily adapts to standard GUI pull-down menu style.
    * (-) Commands have complicated syntax and hard-to-type keystrokes, since a limited number of keys are available for commands.
    * (-) Some needed keys might not be available on all keyboards. 

# Plus and Minus for modes (Vi):

    * (-) Confusion about which mode program is currently in.
    * (-) Nuisance of switching modes frequently.
    * (+) Many more keystrokes (~90) available for commands.
    * (+) Touch typists tend to become very proficient because the fingers can stay in their normal positions almost all the time. 

```

Regards
Iain

---

### Post by wsonar on 2009-04-15
If you start using server edition then you may need to know the basics

on opening a file ,editing a file, and saving a file

---

### Post by Slim Odds on 2009-04-15
First, you should learn a little about VI. Then, a little about EMACS.....

Then..... get ready to rumble!!!!   :lolflag:

(P.S. this is a joke based on the ongoing eternal battle between vi and emacs)

(P.S.S. I used emacs extensively in the past, but now use vim).

---

### Post by Paqman on 2009-04-15
> **wsonar said:**
> If you start using server edition then you may need to know the basics

on opening a file ,editing a file, and saving a file

If that's all you're doing then nano will do the job nicely, and has the shortcuts displayed at the bottom of the screen.

---

### Post by benj1 on 2009-04-15
> **ddrichardson said:**
> 

Anyhoo, hardcore linux users use cat > filename ;-)

no they use a magnetised needle and a steady hand :p


i am very impressed this hasn't descended into a vim v emacs flame war.

---

### Post by wsonar on 2009-04-15
> **Paqman said:**
> If that's all you're doing then nano will do the job nicely, and has the shortcuts displayed at the bottom of the screen.

oh yea forgot about that I had been messing around with BSD and forgot about nano much easier kinda like dos edit

---

### Post by sahabcse on 2009-04-15
vi or vim is powerful command line editor. For knowing more type in terminal

#man vi 



:guitar:

---

### Post by wirelessmonkey on 2009-04-15
> **Slim Odds said:**
> First, you should learn a little about VI. Then, a little about EMACS.....

Then..... get ready to rumble!!!!   :lolflag:

(P.S. this is a joke based on the ongoing eternal battle between vi and emacs)

(P.S.S. I used emacs extensively in the past, but now use vim).

^X-M KILL VIM


<EMACS RUUL3!>

;)  Just in the spirit of the game.
/Flame on

---

### Post by theozzlives on 2009-04-15
It's kinda like edlin was for DOS, I've had to use it when I had to edit something and couldn't get to the GUI. It's also in pretty much in every Linux Distro. For the most part, I use gedit.

vi...edlin
nano...edit
gedit (or Kate)...Notepad

---

### Post by hovzio on 2009-04-15
It depends what your planning on doing. If you are planning on learning something bout linux and working with the command line; then learning some vi can be seen as a " .*nix rite of passage".. I guess. It certainly doesn't harm, somebody mentioned vimtutor above, this is a great place to get started. If you are working with a headless server; emacs or vim, nano.. is an absolute must. For scripting and co I prefer a graphical editor like kate, but thats just personal choice. My opinion to vim; if you know how to use it, it is very time efficient and you can navigate/edit at least at twice the speed as in a gui. The learning curve is quite a bit greater than lets say gedit. IMHO its not to early to look at vi, alone the sparced interest... check it out. :)

---

### Post by stchman on 2009-04-15
> **superplasmafist said:**
> ive read and seen stuff aboput its important to learn vi.

im new to linux and want to learn everything. is this a good place to start or should i learn other stuff first?

i know theres something else called emacsbut that vi is better.

thanks

I have been using Ubuntu for over two years and found ZERO need for vi.  I personally think vi sucks (I know I will get flamed).

The vi editor to me was a bad joke gone wrong.  How it has stuck around this long seems to indicate radical cult following.  The vi editor should be buried deeply in a hole and never thought of again.

The nano text editor for CLI purposes does quite a bit and is far easier to use.

For GUI applications I prefer Geany or Gedit.  They are excellent easy to use text editors with many features.

---

### Post by leandromartinez98 on 2009-04-15
> **stchman said:**
> I have been using Ubuntu for over two years and found ZERO need for vi.  I personally think vi sucks (I know I will get flamed).

The vi editor to me was a bad joke gone wrong.  How it has stuck around this long seems to indicate radical cult following.  The vi editor should be buried deeply in a hole and never thought of again.

The nano text editor for CLI purposes does quite a bit and is far easier to use.

For GUI applications I prefer Geany or Gedit.  They are excellent easy to use text editors with many features.

Let's not start the same old discussion. I've been using Vi/Vim for about 10 years now. Particuarly for touch-typists I've not seen anything as practical. It is, indeed, irritating at first. I also know very skillfull computer programmers that don't like it, so it is not something you NEED, for certain. It is worth a try, on the other side, because people who gets used to it can do things very rapidily and efficently. On the other side, being the most common *nix editor, I find that ultimately everybody that uses other editors turns out to need to use a little bit of vi one day or another, and, on the other side, if you are a heavy vim user probably you won't need anything else.

---

### Post by Arndt on 2009-04-15
> **ddrichardson said:**
> vi is just a text editor. There was a time when there weren't any text editors and then along came vi and nano.


Yes, you're right, there was a time when there weren't any text editors, then came vi (in the 70's), and then came nano (in 1999).

---

### Post by Slim Odds on 2009-04-15
> **Arndt said:**
> Yes, you're right, there was a time when there weren't any text editors, then came vi (in the 70's), and then came nano (in 1999).

EMACS was first released in 1976

---

### Post by ddrichardson on 2009-04-15
> **Arndt said:**
> Yes, you're right, there was a time when there weren't any text editors, then came vi (in the 70's), and then came nano (in 1999).
If you're in the mood for splitting hairs then what we're really talking about is vim (1991 on Amiga) in much the same vein as nano is a clone of pico - used in the pine client which was 1989.

Bill Joy's version of vi in 1976 is not that similar to the standardised terminfo version from Bell Labs in System V which was 1983.

---

### Post by Arndt on 2009-04-16
> **ddrichardson said:**
> If you're in the mood for splitting hairs then what we're really talking about is vim (1991 on Amiga) in much the same vein as nano is a clone of pico - used in the pine client which was 1989.

Bill Joy's version of vi in 1976 is not that similar to the standardised terminfo version from Bell Labs in System V which was 1983.

Splitting hairs is fun but not always helpful. What I wanted to do was to convey the message that the description of history left out quite a bit, and to prevent people from thinking that everything in Linux originated with Linux (but clearly you didn't imply that).

---

### Post by TideMan on 2009-04-16
Isn't vi the editor that comes up when you do:
```
crontab -e
```

Having been brought up on using Wordmaster on CP/M back in the early days of PCs (before a mouse), vi was a breeze.

---

### Post by WhiskyChris on 2009-04-16
The first time you run crontab it gives you a choice of which editor to use so it depends what you pick. I'd imagine you can subsequently change it somehow...

```
$ crontab -e
no crontab for christopher - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /usr/bin/vim.tiny
  2. /bin/ed
  3. /bin/nano        <---- easiest

Choose 1-3 [3]: 
```
(new install for me!)

I always used to use emacs but have just started working somewhere different and one of the servers I use doesn't have emacs or nano on it. That made me figure out vi (which I get very lost in before) and it's not so bad once you figure out the basics. I'm sure I've still got a lot to learn, but once you know how to switch between modes, save and exit you can pretty much learn anything else at whatever pace you need it, if you need it at all - that's a different discussion!

Now I know how to use vi it's what I tend to use for tweaking config files and all sorts.

---

### Post by Japanac033 on 2009-04-16
I hated vi from the beginning and I still hate it.

But I must acknowledge that it is pretty swift for programming. 

However, I prefer syntax highlighting and a easier user interface that comes with Joe

---

### Post by Slim Odds on 2009-04-16
> **Japanac033 said:**
> I hated vi from the beginning and I still hate it.

I think everyone should hate vi, until they understand how to use it.

>  I must acknowledge that it is pretty swift for programming.

Yes, once you understand it, you can really fly.

> However, I prefer syntax highlighting and a easier user interface that comes with Joe

VIM has syntax highlighting and a whole lot more.....

---

### Post by superplasmafist on 2009-04-16
okay im using vi in kubuntu now which is vim.

fun stuff. i also wrote a hello world program for python.

when i learn vim will i be able to use vi?

---

### Post by leandromartinez98 on 2009-04-16
> **superplasmafist said:**
> okay im using vi in kubuntu now which is vim.

fun stuff. i also wrote a hello world program for python.

when i learn vim will i be able to use vi?

Vim is an expanded version of Vi with many more features. If you are used to Vim, you will be able to use Vi, sometimes with the feeling that some useful stuff you are used to is missing.

---

### Post by bp1509 on 2009-04-18
d

---

### Post by bp1509 on 2009-04-18
d

---

### Post by durand on 2009-04-18
@stchman: You obviously haven't given vim a proper try. When I first learned it, it felt really strange and had all these weird key bindings and stuff like that but you do get used to them. You should give vimtutor a try, it really helped me.

@bp1509: I was quite surprised about this but vim wasn't actually preinstalled in gentoo. And they switched visudo to use nano instead in ubuntu which is kinda ironic..Even so, I would think that nano would be on most linux distros now, newbie friendly or not. Despite what you said, I still prefer to use a GUI editor, dependent on what I'm actually trying to do. My main frustration with vim and some other commandline programs is that the cursor jumps from line to line rather than from character to character. If I wanted to go to the same place on the next line, I would need to go to it's start and then move right which is really annoying. Maybe there's a feature I'm missing here?

---

### Post by bp1509 on 2009-04-18
d

---

### Post by xarquid on 2009-04-18
vim is nice to know.

If you're willing to give it a try have some cheatsheets handy :-)

A reference card (.PDF):
[http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf]("http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf")

A few reference guides:
[http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html) (my favorites, graphical and colorful!)
[http://fprintf.net/vimCheatSheet.html](http://fprintf.net/vimCheatSheet.html) (plain text)
[http://www.pixelbeat.org/vim.tips.html](http://www.pixelbeat.org/vim.tips.html) ("essential vim")

Good luck!

---

### Post by bp1509 on 2009-04-18
d

---

### Post by xarquid on 2009-04-18
Great post above by bp1509 as well too! Nice guides.

---

### Post by JK3mp on 2009-04-18
I think the debate here has turned more in the way of a GUI Lovers Vs. Command Line Lovers. Vi is a GREAT command line editor if you prefer to do alot of your work via command line. Also to ME anywho alot faster for editing configuration files that are generally easier to access and edit via the command line. Example :D

```
vi /dir/dir/config.file

```
edit the file(does require pressing "i" to enter Insert Mode then "shift colon wq!"
 to save and exit. 
 
or you could just click click cliick, enter admin password click edit, click save. Idk..the click click option is just to annoying the click click click you can get done in one command line entry. Idk..if you type decent and don't mind command line, its just faster, easier and preffered. What it comes down to is GUI or Terminal?
Another thing is its alot lighter and more common in lightwieght distributions like Arch and Gentoo ones that are built more scratch that allow you to just add what you want and nothing else kinda thing.

---

### Post by xarquid on 2009-04-18
> **JK3mp said:**
> I think the debate here has turned more in the way of a GUI Lovers Vs. Command Line Lovers. Vi is a GREAT command line editor if you prefer to do alot of your work via command line. Also to ME anywho alot faster for editing configuration files that are generally easier to access and edit via the command line. Example :D

```
vi /dir/dir/config.file

```
edit the file(does require pressing "i" to enter Insert Mode then "shift colon wq!"
 to save and exit. 
 
or you could just click click cliick, enter admin password click edit, click save. Idk..the click click option is just to annoying the click click click you can get done in one command line entry. Idk..if you type decent and don't mind command line, its just faster, easier and preffered. What it comes down to is GUI or Terminal?
Another thing is its alot lighter and more common in lightwieght distributions like Arch and Gentoo ones that are built more scratch that allow you to just add what you want and nothing else kinda thing.

Very, very true.

---

### Post by mrowth on 2009-04-18
nm

---

### Post by durand on 2009-04-19
> **bp1509 said:**
> [http://tuxtraining.com/2008/11/13/vi-and-vim-cheatsheets](http://tuxtraining.com/2008/11/13/vi-and-vim-cheatsheets)

[http://tuxtraining.com/tag/vim](http://tuxtraining.com/tag/vim)  there's a ton more here too.  Going character to character is just using the H and L keys in command mode.

Thanks! However, I'm still not sure how to go down the page character by character. I guess I didn't clarify myself very well...For example, if a line was word wrapped, how would I go down to the character below which is actually on the same line?

---

### Post by dmm1983 on 2009-04-19
i started out on vi went to vim
but all linux/unix systems use vi
So be learning vi ur able to use all other linux/unix os's

---

### Post by leandromartinez98 on 2009-04-19
> **durand said:**
> Thanks! However, I'm still not sure how to go down the page character by character. I guess I didn't clarify myself very well...For example, if a line was word wrapped, how would I go down to the character below which is actually on the same line?

To move through "screen" lines, use:  gj, gk, and columns: gl, gh

(on command mode)

---

