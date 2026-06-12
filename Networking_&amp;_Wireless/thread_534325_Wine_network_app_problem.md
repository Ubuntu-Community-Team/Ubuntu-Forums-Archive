---
title: "Wine network app problem"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by oomingmak on 2007-08-25
I've installed Wine in order to run a remote desktop type app called radmin.

The app seems to have installed correctly (it can be launched and configured fine) but when I try to make the connection to my Windows PC I get the following error message in the console:

> err:ntlm:SECUR32_initNTLMSP ntlm_auth was not foundThe program works fine when used to connect two Windows boxes, so it's not a problem with the app itself.

The error message indicates a Windows authentication issue (that would obviously not arise if installed on Windows natively) but I've no idea how to provide Wine with what it needs in order to authenticate and allow the connection to be made. 

A Google search on the above error message only returned 2 results, neither of which had an answer.

I'd be grateful if someone could help.

Thanks.

---

### Post by dark_harmonics on 2007-09-13
I have the same problem using multiple apps in my wine. I loaded ntlm-auth package, followed some directions on how to configure squid, installed the dcom98 and ie4linux packages for wine. I also used wine doors to install some microsoft stuff like the c++ n stuff. I dont think that is related to this problem. I think if nobody has a hint about the correct direction to go with this, i might just wipe my wine install and start over. I did try it with the standard wine and now i added the repos for the new wine and installed it with no sucess.

The funny thing is: I've ran this app before but got farther before it errors out.

The application just for an fyi is: Altiris Deployment Console 6 sp1

---

