---
title: "Windows ISA Server Client connectivity"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by mohenjo on 2008-05-29
Greetings all,

As I'm getting myself familiar with getting my fresh new Ubuntu 8.04 machine connected to my network, I'm running into all sorts of new things to consider when meshing this machine to my Windows Server 03 domain.

Yesterday, with the help of the forums, I found how I can connect to my domain.  Today however I've encountered a more interesting roadblock: Microsoft ISA Server.

I've got an ISA server set up on the perimeter, and each of our windows machines is running the ISA client on the computer.  Has there been any discussion or article printed on how Ubuntu can communicate or connect to the ISA server?

I took Firefox and just added in the proxy information, but that didn't cut it.  There's clearly more to it than I originally estimated.

Much thanks again,

Mohenjo
[SIZE="1"]Slowly but surely being converted to Ubuntu full-time.[/SIZE]

---

### Post by mohenjo on 2008-06-04
I'm sort of updating myself on this issue.

I'm using likewise-open to connect my computer to the domain, and that was done just fine.  I've since told Firefox where my ISA Server is, and on what port it should proxy everything.  Essentially I've had it copy the IE7 settings on my Windows desktop.

Thus far browsing is painfully slow.  It works, but it's slow.  I'm noticing that there are a lot of anonymous web requests which are getting denied access on the ISA server, and domain user requests are getting through.  But browsing is unacceptably slow.

I'm hoping to look further into the ISA logs tomorrow to see if I'm missing something.

---

