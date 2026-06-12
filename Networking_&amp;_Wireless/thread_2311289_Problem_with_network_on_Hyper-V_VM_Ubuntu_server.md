---
title: "Problem with network on Hyper-V VM Ubuntu server"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by adam185 on 2016-01-26
Hello, last days i have problem with my VM on hyper-v on system Ubuntu server. Don't know why, but network randomly disconnect and then after 5-10 seconds randomly connect back. I try to update realtek drivers on VM, on host too but problem still persist. It's possible to fix this please? Thanks.

this is my ping when i lost connection on vm ubuntu

```
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=6ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Request timed out.
Request timed out.
Request timed out.
Request timed out.
Request timed out.
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=9ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Request timed out.
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=6ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=5ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
Reply from 9x.xxx.xx.xx6: bytes=32 time=4ms TTL=58
```

---

