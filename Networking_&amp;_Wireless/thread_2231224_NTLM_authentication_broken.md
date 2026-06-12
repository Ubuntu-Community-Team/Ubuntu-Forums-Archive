---
title: "NTLM authentication broken?"
date: 2014-06-24
forum: Networking &amp; Wireless
---

### Post by Newbunto on 2014-06-24
Recently I noticed that NTLM authentication doesn't seem to work from FireFox any more, at least not for me. I'm not sure when it was last working so I don't know what changes might have caused this.

I run FireFox 30.0 on both Windows, when I have to )-:, and Linux. I am accessing a web site that is implemented using Sharepoint (on a server running Windows). From a Windows client it works. From Linux it *used to* work. From Linux it does not work now.

Here's an example HTTP dialogue captured on Windows.

```
>>>GET /stuff HTTP/1.1
Host: sharepoint
Cookie: WSS_KeepSessionAuthenticated=80
Connection: keep-alive

<<<HTTP/1.1 401 Unauthorized
Server: Microsoft-IIS/7.0
WWW-Authenticate: NTLM

>>>GET /stuff HTTP/1.1
Host: sharepoint
Cookie: WSS_KeepSessionAuthenticated=80
Connection: keep-alive
Authorization: NTLM xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx==

<<<HTTP/1.1 401 Unauthorized
Server: Microsoft-HTTPAPI/2.0
WWW-Authenticate: NTLM about288bytes

>>>GET /stuff HTTP/1.1
Host: sharepoint
Cookie: WSS_KeepSessionAuthenticated=80
Connection: keep-alive
Authorization: NTLM about600bytes

<<<HTTP/1.1 304 Not Modified
Server: Microsoft-IIS/7.0
```

NB: I have removed from the above what I consider to be irrelevant HTTP headers in order to make the dialogue clearer. I have also censored and shortened the actual NTLM messages (which are all base64 encoded and in any case fairly opaque to me).

While I really don't know the NTLM protocol, that all seems reasonable. I would guess that the second request identifies the client and the response to it contains a random challenge. The third request contains the challenge encrypted by the password hash (or something like that) and everyone is happy. (As it happens the client's cached copied of "/stuff" is still valid so after all that to-ing and fro-ing the client just receives a '304'.)

On Linux what *seems* to be happening is that FireFox gives up immediately on getting the first '401'. It just displays the following.

[h=1]Server Error[/h]
      [h=2]401 - Unauthorized: Access is denied due to invalid credentials.[/h]   [h=3]You do not have permission to view this directory or page using the credentials that you supplied.[/h]  
 

I have not so long ago upgraded to Ubuntu 14.04 LTS (by upgrade from 13.10, not as an install from scratch) and FireFox upgrades itself fairly frequently.

Any hints?

Have I lost something that was previously installed?

Is something wrong with the FireFox config? (Various web pages talk about a range of config parameters that might be relevant but I haven't found anything specific.)

Did some software just break?

One oddity in my environment is that 'sharepoint' resolves to 127.0.0.1 and the actual TCP connection is relayed before it hits the real host called 'sharepoint'. However a) it has always been like that and was working previously on Linux b) it works on Windows when done like that.

---

### Post by Newbunto on 2014-06-24
Clearing FireFox cache, history and cookies did not resolve this.

---

