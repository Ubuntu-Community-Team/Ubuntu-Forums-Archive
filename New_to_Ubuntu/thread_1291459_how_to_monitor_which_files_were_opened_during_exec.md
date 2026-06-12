---
title: "how to monitor which files were opened during execution of a process?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-14
Hi
Thank you for reading my question.
I need to findout which files were accessed during the execution of a program. Can you please let me know how to do it?

I can not use system monitor because the process is very short lived and almost nothing is showed in system monitor during he execution.


Thanks.

---

### Post by diesch on 2009-10-14
On the command line:

```
strace -e trace=file -o some_file.log some_program
```

some_file.log contains a list of a file-related system calls made during the execution of some_program

---

### Post by legolas_w on 2009-10-14
Thank you for the reply.
Can you please let me know whether the command logs possible files that are opened by a program invoked by some_program?

For example if some_program is an script which invokes some other script files which will do the actual job?

Thanks.

---

### Post by diesch on 2009-10-14
Use -f with strace to trace the child processes, too:
```

strace -f -e trace=file -o some_file.log some_program

```

---

