---
title: "Managing donwload speeds"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by huggies15 on 2007-08-08
hi, i have a bit of a strange problem, and i dont know how to go about fixing it...
i live in a shared house and we have pretty shity internet connection/router not sure which causes the problem yet, but our internet cuts out if someone downloads at faster than 500kb/s for a length of time... most people are using windows and they cant get speeds over 400 anyway, but 2 of us use ubuntu, and regularly get speeds greater than 500. we were wondering if there was a way to reduces the download speeds to below 500 a bit like in bitttorrent clients, but for the whole system...
i know its backward that we want to limit it, but its the only way the internet doesnt keep cutting out.
anyway, if u have any ideas i would be grateful,

huggies15

edit: i forgot to add that we connect wirelessly... if that makes a difference, and i should also say im using 7.04

---

### Post by kidders on 2007-08-09
Hi there,

Actually, your problem isn't *that* weird ... there are lots of reasons to want to limit the amount of bandwidth a network user is entitled to. The problem though is that it's quite difficult to exercise much control over the speed at which a remote host chooses to send you data, which makes things a little complicated.

Some of the concepts involved can take a little getting used to, but what you want to do is called "traffic shaping". If all your inbound traffic passes through one Linux box (or any other device with traffic shaping capabilities), you should be able to get it to cap the total load on your internet connection at 500kbps.

---

