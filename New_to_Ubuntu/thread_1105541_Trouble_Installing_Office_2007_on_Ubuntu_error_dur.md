---
title: "Trouble Installing Office 2007 on Ubuntu error during install."
date: 2009-03-24
forum: New to Ubuntu
---

### Post by steve101101 on 2009-03-24
I was following all the directions at the website and got to actually running the setup but it gets an error. 

[http://www.programmerfish.com/roffice-2007-in-linux](http://www.programmerfish.com/roffice-2007-in-linux)

here is the code from the terminal:

```

fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a94c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a94c4, 0x28a90c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a94c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a94c4, 0x28a90c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a94c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a94c4, 0x28a90c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a94c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a94c4, 0x28a90c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a94c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a94c4, 0x28a90c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a94c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a94c4, 0x28a90c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a94c4): stub
fixme:ole:NdrCorrelationInitialize (0x28ac034, 0x28abc34, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28ac034): stub
fixme:ole:NdrCorrelationInitialize (0x28aa9f0, 0x28aa5f0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28aa9f0): stub
fixme:ole:NdrCorrelationInitialize (0x28ac46c, 0x28ac06c, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ole:NdrCorrelationFree (0x28ac46c): stub
fixme:ole:NdrCorrelationInitialize (0x28ac504, 0x28ac104, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ole:NdrCorrelationFree (0x28ac504): stub
fixme:ole:NdrCorrelationInitialize (0x28ac2a8, 0x28abea8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ole:NdrCorrelationFree (0x28ac2a8): stub
fixme:ole:NdrCorrelationInitialize (0x28ac2a0, 0x28abea0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28ac2a0): stub
fixme:ole:NdrCorrelationInitialize (0x28ac26c, 0x28abe6c, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28ac26c): stub
fixme:ole:NdrCorrelationInitialize (0x28abe14, 0x28aba14, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abe14): stub
fixme:ole:NdrCorrelationInitialize (0x28abe14, 0x28aba14, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abe14): stub
fixme:ole:NdrCorrelationInitialize (0x28abe14, 0x28aba14, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abe14): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28a92a4, 0x28a8ea4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a92a4): stub
fixme:ole:NdrCorrelationInitialize (0x28abe14, 0x28aba14, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abe14): stub
fixme:ole:NdrCorrelationInitialize (0x28aa7d0, 0x28aa3d0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28aa7d0): stub
fixme:ole:NdrCorrelationInitialize (0x28a9c28, 0x28a9828, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a9c28): stub
fixme:ole:NdrCorrelationInitialize (0x28ac764, 0x28ac364, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ole:NdrCorrelationFree (0x28ac764): stub
fixme:ole:NdrCorrelationInitialize (0x28abffc, 0x28abbfc, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ole:NdrCorrelationFree (0x28abffc): stub
fixme:ole:NdrCorrelationInitialize (0x28abff4, 0x28abbf4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abff4): stub
fixme:ole:NdrCorrelationInitialize (0x28abfc0, 0x28abbc0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abfc0): stub
fixme:ole:NdrCorrelationInitialize (0x28abb68, 0x28ab768, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abb68): stub
fixme:ole:NdrCorrelationInitialize (0x28abb68, 0x28ab768, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abb68): stub
fixme:ole:NdrCorrelationInitialize (0x28abb68, 0x28ab768, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abb68): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28a8ff8, 0x28a8bf8, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a8ff8): stub
fixme:ole:NdrCorrelationInitialize (0x28abb68, 0x28ab768, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28abb68): stub
fixme:ole:NdrCorrelationInitialize (0x28aa524, 0x28aa124, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28aa524): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:ole:NdrCorrelationInitialize (0x28a96a0, 0x28a92a0, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96a0): stub
fixme:ole:NdrCorrelationInitialize (0x28a96c4, 0x28a92c4, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:ole:NdrCorrelationFree (0x28a96c4): stub
fixme:sfc:SFC_3 0
err:ole:create_server class {000c101c-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {000c101c-0000-0000-c000-000000000046} could be created for context 0x4
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0x2a0c6e8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0x240d160,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:NdrCorrelationInitialize (0x28ad44c, 0x28ad04c, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:RpcImpersonateClient ((nil)): stub
fixme:rpc:RpcRevertToSelf stub
fixme:advapi:CheckTokenMembership (0xa8 0x21f9a0 0x9be5d0) stub!
fixme:ole:NdrCorrelationFree (0x28ad44c): stub
fixme:ole:NdrCorrelationInitialize (0x28ad40c, 0x28ad00c, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x28ad3ac, 0x28acfac, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x28ad38c, 0x28acf8c, 1024, 0x0): stub
err:rpc:RpcAssoc_BindConnection rejected bind for reason 0
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!


```

---

### Post by presence1960 on 2009-03-24
Wine is severely limited in what it can run successfully. Either dual boot or run Windows in virtualisation.

---

### Post by steve101101 on 2009-03-24
these directions said it could be done with 8.10 and the latest install of wine. Thats what i dont understand. I assume the author did it successfully.

---

### Post by presence1960 on 2009-03-24
> **steve101101 said:**
> these directions said it could be done with 8.10 and the latest install of wine. Thats what i dont understand. I assume the author did it successfully.

I hear you! I as well as quite a few others were soured by Wine. A windows install or running windows in virtualization is a sure bet to run what you want. That being said and being only my opinion I bet there are some members in here who have done what you are trying to do. Maybe one of them will show up and help you out. Good luck.

---

### Post by steve101101 on 2009-03-24
okay. thanks for your input.

---

### Post by sonu 1807 on 2009-03-24
I am using office within ubuntu (hardy). I set it up by using this tutorial in forum [http://ubuntuforums.org/showthread.php?t=844309&highlight=office+2007](http://ubuntuforums.org/showthread.php?t=844309&highlight=office+2007)... remember to perform step 10 before 9

---

### Post by RikoW on 2009-03-25
Also, make sure, you are trying that with the exact same version of wine used in the how-to you were refering to. The "lastest version of wine" yesterday and today may very well be different versions! :)

For a hassle free installation and running, may I advertise codeweavers crossover office? It's a "commercial" wine version tweaked to run MS Office (and other) products. I run O2007 on it since quite some time and I'm very happy. Need to pay 40 Euro, though.

Or, even better, use OpenOffice, if you don't need anything very specific from MS Office.

Cheers,

           Riko

---

### Post by steve101101 on 2009-03-25
okay. thanks for the advice. Ill give it a go.

---

### Post by UbuntuNerd on 2009-03-25
you can also check [Here](http://my.opera.com/ubuntunerd1/blog/show.dml/2855480)

---

