---
title: "can't make pipe using mkfifo"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by realmoonstruck on 2011-02-02
can anyone please say why the following code fails to run on my computer...

```

#include <stdio.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

int main(int argc, char** argv)
{
	unlink("p1");
	if (mkfifo("p1",0777))
		printf("\nERROR creating pipe");
	int fd1=open("p1",O_WRONLY);
	printf("\nfd=%d",fd1);
	close(fd1);
	return 0;
}

```
it compiles with no error messages but displays no output when run. the program doesn't terminate also.

the code runs perfectly on other computers running Ubuntu.
can anyone point where i'm going wrong?

---

### Post by TeoBigusGeekus on 2011-02-02
You could add the O_NONBLOCK flag when opening the p1 pipe.

---

### Post by realmoonstruck on 2011-02-02
> **TeoBigusGeekus said:**
> You could add the O_NONBLOCK flag when opening the p1 pipe.

thanks a lot, that solves the problem, but could you please explain what is going on

---

### Post by TeoBigusGeekus on 2011-02-02
See [this]("http://pubs.opengroup.org/onlinepubs/009695399/functions/open.html") page.

---

### Post by realmoonstruck on 2011-02-02
thanks lot again :)

---

