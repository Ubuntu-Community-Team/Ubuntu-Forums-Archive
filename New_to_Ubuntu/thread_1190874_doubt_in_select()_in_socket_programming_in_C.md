---
title: "doubt in select() in socket programming in C"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by polarbear12345 on 2009-06-18
suppose my server program has to deal with 1 listening socket and
1 stdin file descriptor eg.
while(1)
{
//select initialization
select(....args....);
if(FD_ISSET(listenfd,&fd_rd))
{
//some initialization
accept();
}
else if(FD_ISSET(stdin_fd,&fd_rd)
{
//do something
I/O functions
}
}

i wanna know if program is blocked in connect() or I/O functions and request for new connection arrives then that request will be stored in buffer maintained by listen() to be processed by select when program control **reenters** select or will it be lost.

similarly what if one of I/O fds become alive while program is blocked in connect() or I/O functions

---

### Post by zeroseven0183 on 2009-06-18
I would suggest that you post this on [Development & Programming sub-forums]("http://ubuntuforums.org/forumdisplay.php?f=310"). The people there will be able to help you.

Sorry, but that's too technical for me. And oh, I already forgot my C programming in college. My goodness...!

---

