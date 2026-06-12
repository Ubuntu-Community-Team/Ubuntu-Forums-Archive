---
title: "View network connections by 'Source' and 'Destination'"
date: 2015-05-04
forum: Networking &amp; Wireless
---

### Post by dozy on 2015-05-04
Hello Everyone,

Does anyone know of a comman-line tool that can show established network connections and **which side initiated the connection?**
It is key that it indicate which side initiated the connection.

*I have looked at quite a number of tools*, none of the ones that I found will give me an output like the following, for already established connections.

[TABLE="width: 300"]
[TR]
[TD]_Source_[/TD]
[TD]_Destination_[/TD]
[/TR]
[TR]
[TD]**192.168.0.100**[/TD]
[TD]192.168.0.110[/TD]
[/TR]
[TR]
[TD]192.168.0.123[/TD]
[TD]**192.168.0.100**[/TD]
[/TR]
[/TABLE]

netstat would be ideal if it would show source/destination instead of local/foreign, since local/foreign does not indicate direction.


Thanks in advance.

---

### Post by papibe on 2015-05-04
Hi dozy.

Take a look at 'iftop':
```
sudo apt-get install iftop
```
Then
```
sudo iftop
```
Hope it helps. Let us know how it goes.
Regards.

---

