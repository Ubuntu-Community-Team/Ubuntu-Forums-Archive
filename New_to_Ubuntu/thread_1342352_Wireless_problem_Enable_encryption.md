---
title: "Wireless problem: Enable encryption?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Aziza Tullia on 2009-11-30
Hello! I know this is a very basic basic question, but it remains a big problem for me!

So a while ago a very Linux-savy friend of mine installed Wicd Network Manager on my computer, which allowed me to connect to the WPA network at my house, and to any unsecured wireless network. However, it prevents me from connecting to any other secured network- and I have since moved! 

Whenever I try to connect to a new and secured wireless network, I am informed that "This network requires encryption to be enabled." which is all fine and dandy, except that I have yet to find a way of enabling encryption on my computer. I also find it curious that I was able to use the encrypted network at my old house, but cannot even get to the password-entry phase anywhere else. But that's not my main concern...

Please, can anyone tell me how to enable encryption on my computer so that I can access the internet at home?

I am running Ubuntu 8.10 on a Dell Inspiron 1501 laptop. 

Thank you in advance and cheers!

---

### Post by stoogiebuncho on 2009-12-06
I don't use Wicd, but it looks like there's an arrow beside the network (in the network list) that you can click to enable encryption (go to "Advanced Settings").

See this thread:
[http://wicd.net/punbb/viewtopic.php?id=616]("http://wicd.net/punbb/viewtopic.php?id=616")

If that fails, I'd try completely removing wicd:
```
sudo apt-get purge wicd
```
And then reinstalling it:
```
sudo apt-get install wicd
```

---

