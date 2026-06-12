---
title: "SMTP question"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Kellemora on 2009-04-27
Hi Gang

I didn't post before checking at least 30 web sites and not finding an answer.

Using Ubuntu Hardy 8.04 running Eudora in Wine successfully for over a year now, with no problems.

I send and receive my e-mail through an outstate ISP, standard POP3 and SMTP protocols, nothing weird.

On occasion (in the past) when I cannot connect to my outstate ISP to send mail, I will use a local POP3 server to connect and it has always worked fine.

Last year I moved up to using Hi Speed Cable (only choice here is Comcast), however, I was still using my SMTP in St. Louis.  
If for some reason I could not Sendmail, I would then use Comcasts SMTP server.

For the past two days, I CAN receive all my inbound mail, but I cannot send outbound mail.  Keeps timing out!  So I switched my SMTP server over to the Comcast SMTP server and it's out too.

Which makes me wonder, since I'm on CABLE, when I SENDMAIL to the SMTP server, even though I may NAME an SMTP server in St. Louis (I'm in Knoxville), IF the Comcast SMTP server is DOWN, does that mean all SMTP access is down to me because of it?

I've tried to study how it works, but cannot find that part of the question and answers.

Or worded more simply, if I set my outbound email SMTP server to a St. Louis ISP and it's always worked THROUGH my Comcast CABLE connection, is that because it's in reality using Comcasts SMTP server, even though I didn't name it as the outbound server.  EG smtp.comcast.net or smtp.stlouis.com (fictitious names).  I would normally use smtp.stlouis.com for my outbound server, even though I'm on Comcast Cable.

It's worked fine ever since getting cable internet!

Call to Comcast on the landline give a message heavy volume try later and they hang up.  That's their NORMAL way of handling calls!

TTUL
Gary

---

### Post by 123456789123456789123456 on 2009-04-27
> **Kellemora said:**
> Hi Gang

I didn't post before checking at least 30 web sites and not finding an answer.

Using Ubuntu Hardy 8.04 running Eudora in Wine successfully for over a year now, with no problems.

I send and receive my e-mail through an outstate ISP, standard POP3 and SMTP protocols, nothing weird.

On occasion (in the past) when I cannot connect to my outstate ISP to send mail, I will use a local POP3 server to connect and it has always worked fine.

Last year I moved up to using Hi Speed Cable (only choice here is Comcast), however, I was still using my SMTP in St. Louis.  
If for some reason I could not Sendmail, I would then use Comcasts SMTP server.

For the past two days, I CAN receive all my inbound mail, but I cannot send outbound mail.  Keeps timing out!  So I switched my SMTP server over to the Comcast SMTP server and it's out too.

Which makes me wonder, since I'm on CABLE, when I SENDMAIL to the SMTP server, even though I may NAME an SMTP server in St. Louis (I'm in Knoxville), IF the Comcast SMTP server is DOWN, does that mean all SMTP access is down to me because of it?

I've tried to study how it works, but cannot find that part of the question and answers.

Or worded more simply, if I set my outbound email SMTP server to a St. Louis ISP and it's always worked THROUGH my Comcast CABLE connection, is that because it's in reality using Comcasts SMTP server, even though I didn't name it as the outbound server.  EG smtp.comcast.net or smtp.stlouis.com (fictitious names).  I would normally use smtp.stlouis.com for my outbound server, even though I'm on Comcast Cable.

It's worked fine ever since getting cable internet!

Call to Comcast on the landline give a message heavy volume try later and they hang up.  That's their NORMAL way of handling calls!

TTUL
Gary

lets see if I can help you out here
first off, POP3 aka (Post Office Protocal verson 3) is the newest protocal used for mail-email
SMTP - simple mail transfer protocal, is the older method, and is not widely used anymore.
If you are using internet and mail access through comcast, you are using there system to contact the other server.  If comcast is no longer accepting SMTP protocal for some reason, it would possible deny access to that other server.
the other server may be down.
you listed above the address to the server.
go to terminal, use ping and the address of the server
does it connect?
if so, attempt connecting to it using firefox, directly through internet.  Instead of http for the header, use smtp as the main part.  so it would be smtp:// and so on.

---

### Post by spikoley on 2009-04-27
Try switching your SMTP server settings to port 587.

---

### Post by Kellemora on 2009-04-27
Hi numbers and Spike

Well after being on hold and cut off most of the day, I found a Live On-Line Tech support area.

They got me fixed up right away!

First they blamed it on ME, hi hi.........
Then they checked and saw they changed my port number during an upgrade.

I hope they don't quit using SMTP because I rarely if ever use web-mail for anything.

I keep hoping Mozilla will port over Eudora to Linux!  I know they attempted it with Thunderbird, but it's still lousy Thunderbird and nothing like the REAL Eudora.  I have the commercial version, lots of features I can't do without that you don't have on the Free or Sponsored versions.  

Thanks Guys - Up and running now!
Finally!

TTUL
Gary

---

