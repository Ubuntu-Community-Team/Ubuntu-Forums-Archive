---
title: "Netstat - Open ports"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by avnd on 2011-06-07
Hello there.

I'm a newbie and I thought that there should be no open ports by default in a fresh Ubuntu install. But as soon as I install and run 'netstat -lptu' i get the following output. Does this mean there are listening ports? Is this normal?

---

### Post by Rubi1200 on 2011-06-07
Hi and welcome to the forums :-)

You are right, Ubuntu does not have any ports open by default:
[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

You need to run the netstat command with sudo to see the full results.

In any event, this post will explain it better than I could:
[http://ubuntuforums.org/showpost.php?p=10837175&postcount=14](http://ubuntuforums.org/showpost.php?p=10837175&postcount=14)

In other words, I don't think you need to be concerned.

Enjoy!

---

### Post by avnd on 2011-06-07
That was a nice discussion you referred me to, Rubi1200. Thank you very much. I actually read the security sticky. But I found it too Greek and Latin being glued to Windows for a long time. Thanks again, mate.

---

### Post by jtarin on 2011-06-07
You can go [here]("https://www.grc.com/x/ne.dll?bh0bkyd2") and see what ports are open from the outside.

---

### Post by Rubi1200 on 2011-06-08
> **avnd said:**
> That was a nice discussion you referred me to, Rubi1200. Thank you very much. I actually read the security sticky. But I found it too Greek and Latin being glued to Windows for a long time. Thanks again, mate.
No problem, you are more than welcome :-)

I am glad you found it useful.

---

