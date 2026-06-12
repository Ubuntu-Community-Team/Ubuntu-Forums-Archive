---
title: "help regarding afbp(alex firewall bypasser )"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by satishkvv on 2009-03-12
while i was trying to install afbp ..it asked for dependencies ..ncurses ..i installed it and again tried to install afbp ...but m getting some errors ...plzzz help 

when i type make these are the errors ....
@ubuntulaptop:~/afbp-0.5.2$ sudo make
-e [LD] ./src/fbpss.o ./src/http.o ./src/tunnel-io.o ./src/choose-proxy.o ./src/curses-ui.o ./src/cmdline.o -> fbpss
./src/curses-ui.o: In function `paintscr':
curses-ui.c.text+0x1ff): undefined reference to `COLS'
curses-ui.c.text+0x266): undefined reference to `mvprintw'
curses-ui.c.text+0x26b): undefined reference to `stdscr'
curses-ui.c.text+0x283): undefined reference to `wattr_on'
curses-ui.c.text+0x288): undefined reference to `COLS'
curses-ui.c.text+0x2e2): undefined reference to `COLS'
curses-ui.c.text+0x324): undefined reference to `mvprintw'
curses-ui.c.text+0x329): undefined reference to `stdscr'
curses-ui.c.text+0x341): undefined reference to `wattr_off'
curses-ui.c.text+0x3a0): undefined reference to `LINES'
curses-ui.c.text+0x4ae): undefined reference to `COLS'
curses-ui.c.text+0x53f): undefined reference to `mvprintw'
curses-ui.c.text+0x5c7): undefined reference to `COLS'
curses-ui.c.text+0x5f9): undefined reference to `mvprintw'
curses-ui.c.text+0x5fe): undefined reference to `stdscr'
curses-ui.c.text+0x616): undefined reference to `wmove'
curses-ui.c.text+0x65c): undefined reference to `COLS'
./src/curses-ui.o: In function `curses_thread':
curses-ui.c.text+0x68c): undefined reference to `initscr'
curses-ui.c.text+0x691): undefined reference to `stdscr'
curses-ui.c.text+0x6aa): undefined reference to `keypad'
curses-ui.c.text+0x6af): undefined reference to `nonl'
curses-ui.c.text+0x6b4): undefined reference to `cbreak'
curses-ui.c.text+0x6b9): undefined reference to `noecho'
curses-ui.c.text+0x70a): undefined reference to `stdscr'
curses-ui.c.text+0x712): undefined reference to `werase'
curses-ui.c.text+0x71c): undefined reference to `stdscr'
curses-ui.c.text+0x724): undefined reference to `wrefresh'
curses-ui.c.text+0x793): undefined reference to `stdscr'
curses-ui.c.text+0x79b): undefined reference to `wgetch'
curses-ui.c.text+0x7ae): undefined reference to `curscr'
curses-ui.c.text+0x7be): undefined reference to `clearok'
./src/curses-ui.o: In function `size_handler':
curses-ui.c.text+0x885): undefined reference to `resizeterm'
curses-ui.c.text+0x88f): undefined reference to `stdscr'
curses-ui.c.text+0x897): undefined reference to `wrefresh'
./src/curse-ui.o: In function `curses_exit':
curses-ui.c.text+0x8a7): undefined reference to `endwin'
collect2: ld returned 1 exit status
make: *** [fbpss] Error 1

---

