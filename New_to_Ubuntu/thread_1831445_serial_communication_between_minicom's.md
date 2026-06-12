---
title: "serial communication between minicom's"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by just_abhi22 on 2011-08-23
hi all
i am having a software to create two virtual serial ports (COM6 & COM7) in my system, which are bridged together. that can be used for serial communication.
when i used both ports using two hyperterminals (on same system), they commonicate very well and i could receive text on both ends.
now, when i try to do same between 2 minicoms, it fails. i could not find any output at any end. 
now when i try to use 1 port by hyperterminal and other at minicom (ubuntu installed at vmware), i could receive output on hyperterminal from minicom but not vice-versa i.e. i could not have output on minicom from hyperterminal.

what is the exact problem??? my settingd for minicom: 9800 8-N-1 no flow

please help me to have two way communication.

thanks

---

### Post by Wim Sturkenboom on 2011-08-23
Do you use that same software? From your other threads, are you communicating between 2 virtual machines? Or two minicons in one virtual machine?

Theoretically you don't need additional software; pseudoterminals do exactly what you want (within one Linux virtual machine).

Ubuntu unfortunately only supports the unix98 style pseudo terminals and not the older style (possibly deprecated) and I haven't managed to get the unix98 style properly going for what you do :(

Communication using the older ones (pttypX and ttypX) is piece of cake and works smoothly; see [http://tldp.org/HOWTO/html_single/Text-Terminal-HOWTO/#ss7.2](http://tldp.org/HOWTO/html_single/Text-Terminal-HOWTO/#ss7.2)

Maybe you can explain what you're trying to achieve; communication between 2 minicoms is not the most useful ;) If this is, like I use it, to figure things out for software development, you might be better of trying it directly in software (only applicable to this specific thread wher only linux is involved)..

---

### Post by just_abhi22 on 2011-08-23
actually, i want to use virtual machine having linux,to be used as target and windows to use as server. i want to send my data from windows using hyperterminal that should be received at minicom in linux virtual machine. reverse is happening. i can send things via minicom to hyperterminal.why not other way??
i was playing with two instances of minicom on same linux machine to analyze issues with minicom sending and receiving but i cud neither send or receive their as well.
not sure where the problem lies.

---

### Post by Wim Sturkenboom on 2011-08-23
// NOTE you posted while I was typing this.

OK, I found the [http://www.linuxquestions.org/questions/linux-general-1/how-to-create-a-virtual-serial-com-port-in-linux-797851/#post4000260](http://www.linuxquestions.org/questions/linux-general-1/how-to-create-a-virtual-serial-com-port-in-linux-797851/#post4000260) on LinuxQuestions to get two minicoms communicating.

Compile the code (instructions at top of the code) and run it. It will display something like

```

wim@desktop-01:~/pseudottytest$ ./tty0tty 
(/dev/pts/2) <=> (/dev/pts/3)

```

Open two terminals.
Start one minicom in one terminal
```

sudo minicom -o -D /dev/pts/2

```
and one in another terminal
```

sudo minicom -o -D /dev/pts/3

```

This definitely solves my problems with unix98 style pseudo terminals. My infinite thanks go to lcgamboa who posted this on LQ.

---

### Post by just_abhi22 on 2011-08-23
please try to be more simpler. i am not linux geek so could not really understand the code,neither could analyze its future effects.
looking for more simpler and effective solutions.:confused:

---

### Post by Wim Sturkenboom on 2011-08-23
Sorry. I incorrectly assumed that you knew a little about this due to the software that you use (that creates fake com ports).

OK, so now my question is why you want hyperterm and minicom to communicate with each other? Just for fun?

Source code provided by lcgamboa
```

/*compile with :  gcc -Wall -O2 -D_GNU_SOURCE tty0tty.c -o tty0tty */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>


int
ptym_open(char *pts_name, char *pts_name_s , int pts_namesz)
{
    char    *ptr;
    int     fdm;

    strncpy(pts_name, "/dev/ptmx", pts_namesz);
    pts_name[pts_namesz - 1] = '\0';

    fdm = posix_openpt(O_RDWR | O_NONBLOCK);
    if (fdm < 0)
        return(-1);
    if (grantpt(fdm) < 0)
    {
        close(fdm);
        return(-2);
    }
    if (unlockpt(fdm) < 0)
    {
        close(fdm);
        return(-3);
    }
    if ((ptr = ptsname(fdm)) == NULL)
    {
        close(fdm);
        return(-4);
    }

    strncpy(pts_name_s, ptr, pts_namesz);
    pts_name[pts_namesz - 1] = '\0';

    return(fdm);
}


int main(void)
{
  char master1[1024];
  char slave1[1024];
  char master2[1024];
  char slave2[1024];

  int fd1;
  int fd2;

  char c1,c2;

  fd1=ptym_open(master1,slave1,1024);

  fd2=ptym_open(master2,slave2,1024);

   printf("(%s) <=> (%s)\n",slave1,slave2);


  while(1)
  {
    if(read (fd1,&c1,1) == 1) write(fd2,&c1,1);
    usleep(20);
    if(read (fd2,&c2,1) == 1) write(fd1,&c2,1);
    usleep(20);
  };

  close(fd1);
  close(fd2);

  return EXIT_SUCCESS;
}

```
Save this as *_tty0tty.c_*.
Next open a terminal, navigate to the directory where the files is saved and run the command below
```

gcc -Wall -O2 -D_GNU_SOURCE tty0tty.c -o tty0tty
```
Ignore the warnings.

---

### Post by just_abhi22 on 2011-08-25
actually, the software i was using to create virtual serial ports was not proper. it was giving me result with hyperterminal-hyperterminal but not with others.

now i am using another software, that is working perfectly fine with hyperterminals-hyperterminal, hyperterminal-minicom & minicom-minicom.
i am posting link for the software,if someone would require,so that they should not suffer due to bad software as i had.
[http://download.cnet.com/Free-Virtual-Serial-Ports-Emulato/3000-2206_4-10836189.html]("http://download.cnet.com/Free-Virtual-Serial-Ports-Emulator/3000-2206_4-10836189.html").

thank you "[Wim Sturkenboom]("http://ubuntuforums.org/member.php?u=5214")" for all ur help n patience.:popcorn:

---

### Post by Wim Sturkenboom on 2011-08-25
You're welcome and thanks for the feedback. Please mark your thread solved using the thread tools just above the first post on this page.

You might want to post the solution in your other threads relating this subject as well and mark them as solved..

---

