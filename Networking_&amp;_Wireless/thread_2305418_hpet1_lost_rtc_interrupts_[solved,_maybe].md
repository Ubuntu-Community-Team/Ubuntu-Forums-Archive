---
title: "hpet1: lost rtc interrupts [solved, maybe]"
date: 2015-12-05
forum: Networking &amp; Wireless
---

### Post by ben aveling on 2015-12-05
There are other threads that are possibly on this topic, but they all seem to be closed.

Basically since I installed linux on this pc (an Asus R103B ultraportable notebook, running an AMD A4), it's had intermittent problems with the network - and it seems to upset the network too - badly enough to knock other machines off the network. 

The obvious error message in the logs is of the form "Dec  5 21:14:00 a4 kernel: [307391.982177] hpet1: lost 19 rtc interrupts"

I think I have finally found a 'fix'. I reduced the rtc interrupt rate, and restarted networking. And since then, it's been absolutely stable. No problems with networking, and no more rtc errors either. Fingers crossed, but it seems to be fixed.

My only concern is that after a reboot, the interrupt rate went back to 1024. I immediately reduced it again. Oddly, the rtc problem didn't come back while the interrupt rate was 1024. It's as if having run at a lower rate once, it's given it a chance to get itself into order. If not, then I'll need to find a way to reduce the rate at startup, perhaps by inserting something ahead the rest of the services starting.

Long story short, if the interrupt rate is high, reducing the interrupt rate can prevent interrupts going missing.

Regards, Ben

PS. There may be a better way to set the interrupt rate, but I used a few lines of C code.

```

#include <errno.h>
#include <linux/rtc.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/ioctl.h>

int read_rtc(int fno)
{
  int request = RTC_IRQP_READ;
  unsigned long resp;
  int i = ioctl(fno, request, &resp);
  printf("read = %d\n",i);
  printf("interrupts = %ld\n",resp);
  return i;
}

int set_rtc(int fno)
{
  int request = RTC_IRQP_SET;
  unsigned long resp=16;
  int i = ioctl(fno, request, resp);
  printf("wrote = %d\n",i);
  return i;
}

main()
{
  const char *path = "/dev/rtc";
  const char *mode = "r+";
  FILE *rtc = fopen(path, mode);
  if(!rtc){
    perror("fopen of rtc failed. (do you need to run sudo?)");
    exit(-1);
  }
  int fno = fileno(rtc);
  read_rtc(fno);
  set_rtc(fno);
  read_rtc(fno);
  return 0;
}


```

---

### Post by ben aveling on 2015-12-06
Too optimistic. Was working perfectly yesterday. Now, back to being bad. It's possibly less bad. But it is again, not good.

grep -c rtc.int /var/log/syslog{,.1} ; zgrep -c rtc /var/log/syslog.*.gz
/var/log/syslog:4705
/var/log/syslog.1:8675
/var/log/syslog.2.gz:1657
/var/log/syslog.3.gz:645
/var/log/syslog.4.gz:25562
/var/log/syslog.5.gz:28086
/var/log/syslog.6.gz:41112
/var/log/syslog.7.gz:10770

Which suggests it's maybe not just my imagination and that it really is 'less bad' that it was, whether it's because of what I did, or just by coincidence. But how to get it from less bad to good?

---

