---
title: "RTL8723BE wifi drops and won't reconnect till reboot"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by soumoks on 2015-01-15
I found a couple of links about  problems with this particular wifi card but some deal with kernel changes e.t.c
As i've mentioned in the title, Wifi drops after half an hour of usage and won't reconnect till reboot.
any solutions?

Here is the output of the script.
[http://pastie.org/9833906](http://pastie.org/9833906)

---

### Post by soumoks on 2015-01-15
Edit : sorry for not searching earlier but found a similar thread located at
[http://ubuntuforums.org/showthread.php?t=2243978](http://ubuntuforums.org/showthread.php?t=2243978)
ran the following command 
<code>
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
</code>/
Is this enough ? as there are talks of installing a separate backported driver in the same thread?

Thanks

---

### Post by soumoks on 2015-01-17
Apparently this command did the trick as I haven't experienced a wifi drop all day. Hope this helps someone else with the same problem :)
```

echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf

```

---

