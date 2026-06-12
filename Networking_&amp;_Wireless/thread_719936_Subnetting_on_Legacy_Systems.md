---
title: "Subnetting on Legacy Systems"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-03-09
On the issue of using subnet zero and the all-ones subnet, RFC 1878 states, "This practice (of excluding all-zeros and all-ones subnets) is obsolete. Modern software will be able to utilize all definable networks." Today, the use of subnet zero and the all-ones subnet is generally accepted and most vendors support their use. However, on certain networks, particularly the ones using legacy software, the use of subnet zero and the all-ones subnet can lead to problems.

Why is this?  It sounds to me metaphorically like a Y2K problem - like the people who wrote software just reserved X digits, and not X+8 digits.  Please explain, and be specific as possible.

---

### Post by koenn on 2008-03-09
I think it was just an arbitrary decision as to whether zero and all-ones subnets would be used or not. 
If software was build on the assumption they wouldn't be used, I guess the software could be made simpler because the programmer wouldn't have to deal with edge-cases. simpler means less development time & a smaller program, and smaller programs were probably easier to fit on the chips of those days. 
I'm not a programmer so that's as specific as I can get.

---

### Post by MaindotC on 2008-03-09
Edge-cases are like the [all 0's] case and [all 1's] case described above?  Thank you for your prompt reply :)

---

### Post by koenn on 2008-03-10
yes, that' what I meant

---

