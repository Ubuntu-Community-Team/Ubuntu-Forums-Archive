---
title: "'make menuconfig' doesn't work when installing driver for ACX100"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by jerseyboy91 on 2007-03-17
I've been trying to install the ACX100 laptop card on my old laptop's Xubuntu system, but when I type in 'make menuconfig' in the Terminal, it finishes some stuff, but then it screws up on the checklist and dialog files when I try to configure and compile the kernel...

```
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/mconf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:31:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘use_colors’
scripts/kconfig/lxdialog/dialog.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘use_shadow’
scripts/kconfig/lxdialog/dialog.h:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘attributes’
scripts/kconfig/lxdialog/dialog.h:143: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:146: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:147: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:148: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:149: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:151: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:31: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:59: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:95: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c: In function ‘dialog_checklist’:
scripts/kconfig/lxdialog/checklist.c:117: error: ‘WINDOW’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:117: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:117: error: ‘dialog’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: ‘list’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:117: warning: statement with no effect
scripts/kconfig/lxdialog/checklist.c:121: warning: implicit declaration of function ‘endwin’
scripts/kconfig/lxdialog/checklist.c:122: warning: implicit declaration of function ‘fprintf’
scripts/kconfig/lxdialog/checklist.c:122: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/kconfig/lxdialog/checklist.c:122: error: ‘stderr’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: error: ‘COLS’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:141: error: ‘LINES’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function ‘draw_shadow’
scripts/kconfig/lxdialog/checklist.c:143: error: ‘stdscr’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function ‘newwin’
scripts/kconfig/lxdialog/checklist.c:146: warning: implicit declaration of function ‘keypad’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘TRUE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function ‘draw_box’
scripts/kconfig/lxdialog/checklist.c:148: error: ‘attributes’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:149: warning: implicit declaration of function ‘wattrset’
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function ‘mvwaddch’
scripts/kconfig/lxdialog/checklist.c:152: warning: implicit declaration of function ‘waddch’
scripts/kconfig/lxdialog/checklist.c:156: warning: implicit declaration of function ‘print_title’
scripts/kconfig/lxdialog/checklist.c:159: warning: implicit declaration of function ‘print_autowrap’
scripts/kconfig/lxdialog/checklist.c:166: warning: implicit declaration of function ‘subwin’
scripts/kconfig/lxdialog/checklist.c:190: warning: implicit declaration of function ‘print_item’
scripts/kconfig/lxdialog/checklist.c:194: warning: implicit declaration of function ‘print_arrows’
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function ‘print_buttons’
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function ‘wnoutrefresh’
scripts/kconfig/lxdialog/checklist.c:201: warning: implicit declaration of function ‘doupdate’
scripts/kconfig/lxdialog/checklist.c:204: warning: implicit declaration of function ‘wgetch’
scripts/kconfig/lxdialog/checklist.c:211: error: ‘KEY_UP’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:211: error: ‘KEY_DOWN’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: error: ‘FALSE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function ‘scrollok’
scripts/kconfig/lxdialog/checklist.c:223: warning: implicit declaration of function ‘wscrl’
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function ‘wrefresh’
scripts/kconfig/lxdialog/checklist.c:282: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/kconfig/lxdialog/checklist.c:283: warning: implicit declaration of function ‘delwin’
scripts/kconfig/lxdialog/checklist.c:287: error: ‘KEY_LEFT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:288: error: ‘KEY_RIGHT’ undeclared (first use in this function)
make[2]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2
```
I've made some progress in getting the Internet to work on this old laptop, but right now, this is the last step I have to do to enable the wireless function of my laptop card.

---

### Post by lloyd_b on 2007-03-17
(You don't mention which version of Xubuntu you're using.  The following is the correct info for Edgy (6.10), but will probably work on Dapper (6.06) or Fiesty (7.??).)

You need to install the package "libncurses5-dev".  I'm not certain, but I suspect that it's available on the installation CD. 

Lloyd B.

---

