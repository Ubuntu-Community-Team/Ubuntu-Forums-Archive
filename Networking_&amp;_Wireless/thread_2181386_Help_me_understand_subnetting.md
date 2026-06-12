---
title: "Help me understand subnetting"
date: 2013-10-17
forum: Networking &amp; Wireless
---

### Post by Cursed_Lemon on 2013-10-17
I feel like I'm having a little trouble understanding the concept of subnetting. I get the general idea, but I'm not sure I understand how it's implemented. 

My grasp of it so far is that you have a given IP address, let's say you have an IP address 192.143.217.10, which in binary is 11000000.10001111.11011001.00001010.

A netmask (in this case, a subnet mask) is then applied, or the IP is weighed against a subnet mask to determine what subnet it is on. 

The common subnet of 255.255.255.0 would, in this instance, imply that 192.143.217 is the network prefix, and that anything within the last octet is the host identifier. 

This is so because 255.255.255.0 translates as 11111111.11111111.11111111.00000000, where the leading 1s mark the network prefix, and the trailing zeroes mark the host identifier. 

Thus, there are a limited amount of subnet designations because subnets come out as 2[SUP]n[/SUP], where "n" is the number of bits of the network prefix. 

In another example, with a subnet of 11111111.11111111.11110000.00000000 which comes out as 255.255.240.0, let's say we look at the IP of 11000000.10001111.11001001.00001010, which comes out to be 192.143.201.10. 

This would not be on the same subnet as 192.143.217.10 because:

11000000.10001111.110**1**1001.00001010
11000000.10001111.110**0**1001.00001010

The bolded bit is different, which indicates that the second IP would fall under the subnet of 11111111.11111111.11100000.00000000 (255.255.224.0) or less. 

Am I correct in my thinking, here?

---

### Post by SeijiSensei on 2013-10-17
Yes.

---

### Post by houstonbofh on 2013-10-17
Play around with the app here.  [http://www.subnet-calculator.com/](http://www.subnet-calculator.com/)  It uses all forms of notation, so it is easy to visualize a Class C is a /24 is a 255.255.255.0 is a 110nnnnn.nnnnnnnn.nnnnnnnn.hhhhhhhh

---

### Post by Cursed_Lemon on 2013-10-17
That's a great tool! Thanks. :)

---

