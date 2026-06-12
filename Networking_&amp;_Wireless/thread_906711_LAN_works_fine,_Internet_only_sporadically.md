---
title: "LAN works fine, Internet only sporadically"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by arke on 2008-08-31
Hi,

I've got a Linksys WRT54G Router set up with firewall on and no blocks at all. 

My laptop (running XP) works fine both doing LAN and WAN stuff, however the fresh desktop computer I just installed kubuntu on has a few problems. In it, LAN works as expected, WAN only sporadically. I've tried about a billion things, googled a bit, and am pretty much stumped. It will pretty much always ping, but most of the time it will time out and/or take forever doing the DNS lookup. I've yet to find a pattern to this, so as far as I can tell it's random.

The Computer has a MSI motherboard (K8 Neo 4 F I believe, though I'm not sure) with a NVidia CK804 chipset on-board Ethernet controller. I'm running the most recent x64 version of Kubuntu. 

In order to diagnose this a bit more, I wrote a C program which runs timed connection tests. I've appended the code to this post (EDIT: the Test_run() function has all the interesting bits). Here is a run which is 10 iterations of connecting to google on port 80 (I've cut out the parts that aren't relevant):

```

chris@arke-proserpina:~$ ./nettest google.com 80 10
149:    Running test on host google.com with port 80
132:                    TEST_RESULT_GETHOSTBYNAME: 5055ms average
133:                    TEST_RESULT_CONNECT: 3157ms average
149:    Running test on host google.com with port 80
186:            connect() failed: Connection timed out
132:                    TEST_RESULT_GETHOSTBYNAME: 20049ms average
133:                    TEST_RESULT_CONNECT: 188998ms average
149:    Running test on host google.com with port 80
186:            connect() failed: Connection timed out
132:                    TEST_RESULT_GETHOSTBYNAME: 5055ms average
133:                    TEST_RESULT_CONNECT: 188997ms average
149:    Running test on host google.com with port 80
186:            connect() failed: Connection timed out
132:                    TEST_RESULT_GETHOSTBYNAME: 50ms average
133:                    TEST_RESULT_CONNECT: 188998ms average
149:    Running test on host google.com with port 80
132:                    TEST_RESULT_GETHOSTBYNAME: 53ms average
133:                    TEST_RESULT_CONNECT: 161ms average
149:    Running test on host google.com with port 80
132:                    TEST_RESULT_GETHOSTBYNAME: 57ms average
133:                    TEST_RESULT_CONNECT: 159ms average
149:    Running test on host google.com with port 80
132:                    TEST_RESULT_GETHOSTBYNAME: 57ms average
133:                    TEST_RESULT_CONNECT: 163ms average
149:    Running test on host google.com with port 80
132:                    TEST_RESULT_GETHOSTBYNAME: 57ms average
133:                    TEST_RESULT_CONNECT: 158ms average
149:    Running test on host google.com with port 80
186:            connect() failed: Connection timed out
132:                    TEST_RESULT_GETHOSTBYNAME: 5055ms average
133:                    TEST_RESULT_CONNECT: 189000ms average
149:    Running test on host google.com with port 80
186:            connect() failed: Connection timed out
132:                    TEST_RESULT_GETHOSTBYNAME: 54ms average
133:                    TEST_RESULT_CONNECT: 188998ms average
132:    TEST_RESULT_GETHOSTBYNAME: 3554ms average
133:    TEST_RESULT_CONNECT: 94878ms average

```

The uninteresting data here is that connection fails 5 out of 10 times. The more interesting things, however, are the times for gethostbyname() and connect(). gethostbyname() (which does a DNS lookup) takes a very long time (5-20 seconds) 4 out of 10 times, and connect always fails due to a timeout. I don't know what to do anymore, but I'm hoping somebody else might find this info useful and can give me some pointers on how I might fix this (or if its fixable). I don't suspect the network card since everything on LAN works fine. I could imagine it being some sort of odd DNS problem. 

Please let me know if you need any more info, and thanks in advance. -- Chris

```

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <stdio.h>
#include <stdlib.h>
#include <stdarg.h>
#include <strings.h>
#include <unistd.h>
#include <sys/timeb.h>
#include <string.h>
#include <netdb.h>
#include <errno.h>

typedef unsigned long long ms_t;
typedef unsigned int uint;

ms_t timeb_to_ms(struct timeb* tb)
{
	ms_t ms = 0;

	ms += (ms_t) tb->time * 1000;
	ms += (ms_t) tb->millitm;
	return ms;
}

////////////////////////////////////////////////////////////////

typedef struct Timer_s 
{
	struct timeb before;
	struct timeb after;
} Timer;

void Timer_start(Timer* t)
{
	ftime(&t->before);	
}

void Timer_stop(Timer* t)
{
	ftime(&t->after);
}

ms_t Timer_getResult(Timer* t)
{
	ms_t before, after;
	before = timeb_to_ms(&t->before);
	after = timeb_to_ms(&t->after);
	return after - before;
}

////////////////////////////////////////////////////////////////

uint Log_indentLevel = 0;

void Log_indent()
{
	Log_indentLevel++;
}

void Log_unindent()
{
	Log_indentLevel--;
}

void Log_write_(uint lineNumber, const char* format, ...)
{
	uint i;
	va_list ap;
	
	printf("%d:\t", lineNumber);
	for(i = 0; i < Log_indentLevel; i++)
	{
		putchar('\t');
	}
	
	va_start(ap, format);
	vprintf(format, ap);
	va_end(ap);
	
	putchar('\n');
}

#define Log_write(...) Log_write_(__LINE__, __VA_ARGS__)

////////////////////////////////////////////////////////////////

enum {
	TEST_RESULT_SOCKET,
	TEST_RESULT_GETHOSTBYNAME,
	TEST_RESULT_CONNECT,
	TEST_RESULT_SHUTDOWN,
	TEST_RESULT_CLOSE,

	NUM_TEST_RESULT,
};

typedef struct Test_Result_s
{
	ms_t res[NUM_TEST_RESULT];
} Test_Result;

void Test_addResult(Test_Result* a, const Test_Result* b)
{
	uint i;
	for(i = 0; i < NUM_TEST_RESULT; i++)
	{
		a->res[i] += b->res[i];
	}
}

void Test_clearResult(Test_Result* a)
{
	memset(a, 0, sizeof(Test_Result)); 
}

void Test_divideResultScalar(Test_Result* res, ms_t scalar)
{
	uint i;
	for(i = 0; i < NUM_TEST_RESULT; i++)
	{
		res->res[i] /= scalar;
	}
}

void Test_printResult(Test_Result* res)
{
#define RESULT(_w) Log_write("%s: %dms average", #_w, (uint) res->res[_w]);

	RESULT(TEST_RESULT_SOCKET);
	RESULT(TEST_RESULT_GETHOSTBYNAME);
	RESULT(TEST_RESULT_CONNECT);
	RESULT(TEST_RESULT_SHUTDOWN);
	RESULT(TEST_RESULT_CLOSE);

#undef RESULT
}

void Test_run(Test_Result* res, const char* host, int port)
{
	int fd;
	struct sockaddr_in sockAddr;
	int i;
	struct hostent* hostInfo;
	Timer t;

	Test_clearResult(res);
	Log_write("Running test on host %s with port %d", host, port);
	Log_indent();

	Log_write("socket(PF_INET, SOCK_STREAM, 0)");
	Timer_start(&t);
	fd = socket(PF_INET, SOCK_STREAM, 0);
	Timer_stop(&t);
	res->res[TEST_RESULT_SOCKET] = Timer_getResult(&t);
	if(fd < 0)
	{
		Log_write("socket() failed: %s", strerror(errno));
		goto done;
	}

	Log_write("gethostbyname(%s)", host);
	Timer_start(&t);
	hostInfo = gethostbyname(host);
	Timer_stop(&t);
	res->res[TEST_RESULT_GETHOSTBYNAME] = Timer_getResult(&t);
	if(hostInfo == NULL)
	{
		Log_write("gethostbyname() failed: %s", strerror(errno));
		goto done;
	}

	memset(&sockAddr, 0, sizeof(sockAddr));
	sockAddr.sin_family = PF_INET;
	sockAddr.sin_port = htons(port);
	memcpy(&sockAddr.sin_addr.s_addr, hostInfo->h_addr_list[0], sizeof(sockAddr.sin_addr.s_addr));
	
	Log_write("connect(fd, (const void*) &sockAddr, sizeof(sockAddr));");
	Timer_start(&t);
	i = connect(fd, (const void*) &sockAddr, sizeof(sockAddr));
	Timer_stop(&t);
	res->res[TEST_RESULT_CONNECT] = Timer_getResult(&t);
	if(i < 0)
	{
		Log_write("connect() failed: %s", strerror(errno));
		goto done;
	}

	Log_write("shutdown(fd, SHUT_RDWR);");
	Timer_start(&t);
	shutdown(fd, SHUT_RDWR);	
	Timer_stop(&t);
	res->res[TEST_RESULT_SHUTDOWN] = Timer_getResult(&t);

	Log_write("close(fd);");
	Timer_start(&t);
	close(fd);
	Timer_stop(&t);
	res->res[TEST_RESULT_CLOSE] = Timer_getResult(&t);

done:

	Log_indent();
	Test_printResult(res);
	Log_unindent();
	Log_unindent();
}

void Test_runIterations(Test_Result* res, uint num, const char* host, int port)
{
	Test_Result ir;
	uint i = num;

	Test_clearResult(res);

	while(i--)
	{
		Test_run(&ir, host, port);
		Test_addResult(res, &ir);
	}

	if(num != 0) 
	{
		Test_divideResultScalar(res, num);
	}
}

////////////////////////////////////////////////////////////////

int main(int argc, char** argv)
{
	uint i;
	Test_Result res;
	
	if(argc != 4) 
	{
		printf("%s <host> <port> <num iterations>\n", argv[0]);
		return 1;
	}


	Test_runIterations(&res, atoi(argv[3]), argv[1], atoi(argv[2]));

	printf("\n\nTest Results: \n");

	Test_printResult(&res);
	
	return 0;
}



```

---

