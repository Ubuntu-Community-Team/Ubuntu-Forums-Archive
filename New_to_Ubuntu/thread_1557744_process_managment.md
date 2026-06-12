---
title: "process managment"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by abhishek.biradar on 2010-08-21
Difference between kill and kill -9

---

### Post by sharathcshekhar on 2010-08-21
kill sends a SIGTERM signal to the process, which allows the process to do some clean up and exit graciously.
kill -9 sends Signal 9, SIGKILL to the process. This signal cannot be caught and will force the application to terminate immediatley which may cause some loss of data.
Similar to kill -9, you can send any signal to the application like kill -11
If no signal is mentioned, SIGTERM is sent.

---

### Post by corrytonapple on 2010-08-21
Please combine your two questions next time.

---

