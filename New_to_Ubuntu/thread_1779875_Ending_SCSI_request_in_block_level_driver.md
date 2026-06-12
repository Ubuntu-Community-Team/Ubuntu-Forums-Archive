---
title: "Ending SCSI request in block level driver"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by coeteam on 2011-06-11
hi,

We are currently working on block level driver in linux ubuntu .we are having a storage controller and we are trying to capture and filling the scsi requests to a particular  LUN.  

We are trying to mask a  request for that LUN. We were able to get LUN id of hard drive. Our objective is to restrict all the request for that particular LUN at the block level.

We tried to end the request using blk_end_request/blk_end_request_all  when the request is to the LUN id that we are trying to mask , 
but while trying this our server got hanged.

SO Please help us , how to end the request for particular LUN without ending other request for other LUNs.Because all the scsi requests are going thorugh do_cciss_request only.
 
Thanks in Advance

---

