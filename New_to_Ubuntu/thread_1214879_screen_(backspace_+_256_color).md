---
title: "screen (backspace + 256 color)"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by disappearedng on 2009-07-16
hey everyone
I am a beginner, and I am having a little trouble with screen. 

I use vim exclusively, and right now I am using screen for ssh sessions to do batch jobs. 

My vim is configured to display 256 colors, and I have added set t_Co=256
 into my $HOME/.vimrc file. (which displays properly, i can't remember the library that I installed for this).

When I use screen, i realize that the colors no longer displays properly. Any ways to work around this??

2) My second issue is with the backspace problem in screen.

I have tried the following methods suggested online:
1) modifying Xdefaults
2) alias screen='TERM=screen screen'
3) bindkey -d -k kb stuff "\010"

And sadly, nothing works. 
The only solution that I found is with setting my current profile's compatiblity option to Ctrl-H. However, this screws up my vim. So every time I use vim, I have to change it back which is annoying. 

Any work around this?

---

### Post by disappearedng on 2009-07-16
hardy btw

---

