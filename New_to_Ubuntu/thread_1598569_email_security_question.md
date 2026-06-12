---
title: "email security question"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by KWLLC on 2010-10-16
I have just moved to Ubuntu as my full-time environment. I had been using XPpro Firefox and Thunderbird. and used ZoneAlarm for my firewall. I realize now that I don't know what the security needs are for using Ubuntu. ZA provided a one-stop suite for security so I haven't felt the need to stay on top of the current issues and now I'm afraid I've already gotten hit. A bunch of undeliverable emails appeared this am saying I was the sender.
If addon security is needed for my box, what are your recommendations?

Here are the headers:
Return-Path: [EMAIL="dwaldoanderson@yahoo.com"]<dwaldoanderson@yahoo.com>[/EMAIL] Received: (qmail 27392 invoked by uid 60001); 15 Oct 2010 22:15:21 -0000 DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed; d=yahoo.com; s=s1024; t=1287180921; bh=AxnDmQs4V19eDoAXk0O0q2Dp4Xs8CvCOBQmp1zTZvEc=; h=Message-ID:X-YMail-OSG:Received:X-Mailer:Date:From:Reply-To:To:MIME-Version:Content-Type; b=BVOxI5mXFD+jo1JtRSHtqkiyNiSMcrsZn8bOKbGv5bsJQG3NDRWCDKIl0TlqLuxUqYp5ZeFeLxHuT2/UTlmMlvElGDo+SWUIP04IgiXJZzT9mXY0eeuWP93bziETwBmWNvyfATIxJcZZ85Cc6fnVQcB20422VUl0WtICVFP3qR4= DomainKey-Signature:a=rsa-sha1; q=dns; c=nofws;   s=s1024; d=yahoo.com;   h=Message-ID:X-YMail-OSG:Received:X-Mailer:Date:From:Reply-To:To:MIME-Version:Content-Type;   b=p+5y182oQpjwNAVKch5U8lq4o8XhKjTRkhot238a7vwMxGk6l9UYn7oVjDn4ba8+g/NmVv33YadnsTfl2l74AR1aFvwD2neXyZloK7mF4602aKoZ5uTWMDOVEqFAnpotk9GiekMwVr05/Qn4rhbpFeSBPvb/0tWOy3Xnb3BIGJk=; Message-ID: [SIZE=6][EMAIL="351174.11675.qm@web53402.mail.re2.yahoo.com"]<351174.11675.qm@web53402.mail.re2.yahoo.com>[/EMAIL][/SIZE] X-YMail-OSG: 2GedJm0VM1mGFlQ.MJe4nWk0iXrC7ahPyPmzAC9x_GzQKNQ  kWiuxfGGf4Uzq1zwUTMc1K17QGIef3vHpQIBLzYuAbKyQXxQ1EAYtMRTVqIN  LoqgVpwgpiigg1HNZ5cBXFBPxBYVylzWXNvlGSgSZPteIrTL98MHbnLx6Fan  DRSf3OwZ.YV1nMZq7tZRQmhTDjXLVwiANUlLiI94QhVjOug7Q76eUGitMLbz  jMgUJacaI8I.6hIk24mnmhKiOgh3H1wOsE.M1YtKhHz9WdNBtlQmcE9YVmRO  V76CQm0U0vYc7wHIMrvCOR9yvjspkrSt4VOt9KGBI5tSlQ7cE3nUPCc2CXAr  kXuwVeQuXTBlHDc0Gn0VBmNUbwjri Received: from [189.234.143.145] by web53402.mail.re2.yahoo.com via HTTP; Fri, 15 Oct 2010 15:15:20 PDT X-Mailer: YahooMailClassic/11.4.9 YahooMailWebService/0.8.106.282862 Date: Fri, 15 Oct 2010 15:15:20 -0700 (PDT) From: [EMAIL="dwaldoanderson@yahoo.com"]dwaldoanderson@yahoo.com[/EMAIL] Reply-To: [EMAIL="dwaldoanderson@yahoo.com"]dwaldoanderson@yahoo.com[/EMAIL] To: [EMAIL="billpay@billpay.bankofamerica.com"]billpay@billpay.bankofamerica.com[/EMAIL], [EMAIL="Learning@home.lhh.com"]Learning@home.lhh.com[/EMAIL], 
[EMAIL="CHUCK.UTERMOHLEN@usbank.com"] 2345[/EMAIL]3424234342[EMAIL="CHUCK.UTERMOHLEN@usbank.com"] N@usbank.com[/EMAIL], [EMAIL="wbcampaigns@wildblue.com"]wbcampaigns@wildblue.com[/EMAIL],   [EMAIL="connections@*************"]connections@*************[/EMAIL], [EMAIL="jcoomer@commspeed.net"]jcoomer@commspeed.net[/EMAIL],#$%$%$[EMAIL="cramd@wi.rr.com"]@wi.rr.com[/EMAIL] MIME-Version: 1.0 Content-Type: text/plain; charset=us-ascii  [http://paverih.t35.com/](http://paverih.t35.com/)  

Am I correct in thinking that the large-type address in the header is the source of the hijack?

---

### Post by ubudog on 2010-10-16
Bodhi.zazen has a great thread on security in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by lisati on 2010-10-16
The information you have highlighted is a (theoretically) unique identifier for the message. Sometimes it provides a clue to the source, often it doesn't.

A good way of identifying the source of a message is to look at the "received" headers. These, in theory, provide a record of what might be called a "chain of custody" for the message. Usually the last one is the one that indicates where the message came from.

(I'd also suggest putting [noparse]>  at the start of your headers, and [/noparse] after the headers. This can help makie it easier to read.)

---

