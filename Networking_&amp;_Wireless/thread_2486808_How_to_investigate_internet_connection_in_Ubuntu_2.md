---
title: "How to investigate internet connection in Ubuntu 22.04?"
date: 2023-05-11
forum: Networking &amp; Wireless
---

### Post by marrocs on 2023-05-11
Hi everyone

In the past few days the internet connection in my laptop (dell  vostro 3550/ubuntu 22.04) became pretty slow, while in my phone  (android) has been normal.


 I watch tcptrack and speed keep between 0 and 50KB/s.



  But, if i restart network with "systemctl restart  NetworkManager.service", the velocity goes up to 1MB/s for a while after  being drop again.


 

 And this is the return of one general speed test on the internet about a few minutes ago:


 

 Does anyone knows how to troubleshoot this problem?



 Thanks

---

### Post by mIk3_08 on 2023-05-11
> **marrocs said:**
> Hi everyone

In the past few days the internet connection in my laptop (dell  vostro 3550/ubuntu 22.04) became pretty slow, while in my phone  (android) has been normal.

 I watch tcptrack and speed keep between 0 and 50KB/s.

  But, if i restart network with "systemctl restart  NetworkManager.service", the velocity goes up to 1MB/s for a while after  being drop again.

 And this is the return of one general speed test on the internet about a few minutes ago:

 Does anyone knows how to troubleshoot this problem?

 Thanks
For me, I experience very slow internet due to the ISP that I used.  Actually, I have 3 ISP that I used. Two of them uses LTE (for travel  purposes) and the one is a fiber cable connection. In my two LTE  connections, I rarely encounter very slow internet but it will return to  normal speed which I can perform my online job normally. In my fiber  cable connections, I also sometimes encounter slow internet speed maybe  because of maintenance activities of the ISP. When I encounter very slow  internet I just check it via "speedtest-cli". Regards and cheers

---

