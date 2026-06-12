---
title: "Need help understanding ps command"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-21
I found a script and modified it here to check if my java process is running:


```
LOAD=`ps aux | grep internetcheck.jar | wc -l`

if [ $LOAD = 1 ]
then
echo "Failed to launch: Internet Checker already running"
exit 1
fi

echo "Running recheck..."
/home/windsor/workspaces/java/internetcheck.jar -rc

```It sort of works, the problem however is this:
The java process calls Thread.sleep(2000) often, which means that it waits for 2 seconds and does nothing. When this happens, `ps aux | grep internetcheck.jar` cannot find the process! Which isn't what I want at all, I want to know if it is running, or if it is terminated. Can anyone help a nooby out with this issue? Thanks.

---

### Post by r-senior on 2010-03-21
I just tried a test case for this:

```
public class Test {

	public static void main(String ... args) throws Exception {
		while (true) {
			System.out.println("Hello World");
			Thread.sleep(10000);
		}
	}

}
```

Then a brute force test to try and replicate the problem:

$ while true; do (ps aux | grep Test | wc -l); done

The output I get is:

```

1
2
1
1
1
1

```

So, on the face of it, the same problem. I modified the test to check:

$ while true; do (ps aux | grep Test; echo); done

and I get this:

```

r-senior   8993  0.0  2.0 210888 10680 pts/0    Sl+  00:02   0:01 java Test

r-senior   8993  0.0  2.0 210888 10680 pts/0    Sl+  00:02   0:01 java Test

[COLOR="Red"]r-senior   8993  0.0  2.0 210888 10680 pts/0    Sl+  00:02   0:01 java Test
r-senior  12420  0.0  0.1   3040   800 pts/1    S+   00:28   0:00 grep --color=auto Test[/COLOR]

[COLOR="Red"]r-senior   8993  0.0  2.0 210888 10680 pts/0    Sl+  00:02   0:01 java Test
r-senior  12423  0.0  0.1   3040   804 pts/1    S+   00:28   0:00 grep --color=auto Test[/COLOR]

r-senior   8993  0.0  2.0 210888 10680 pts/0    Sl+  00:02   0:01 java Test

r-senior   8993  0.0  2.0 210888 10680 pts/0    Sl+  00:02   0:01 java Test

```

On that basis, it looks like the inconsistency is not whether ps picks up the Java process, it's whether ps picks up the grep.

There is possibly a more elegant way around this but the following gives me consistent results because the process listing of grep itself includes the "$" but the "$" in the pattern matches EOL:

$ while true; do (ps aux | grep Test$; echo); done

---

### Post by TurnOfTide on 2010-03-22
Nice, much thanks man for your time you put into that. :popcorn:

---

### Post by undecim on 2010-03-22
Whenever I want a "ps aux | grep foo" command to ignore grep, I always use brackets, and get "ps aux | grep [f]oo" the brackets don't effect the search string, but the process is called without the exact string, so it never finds itself.

Of course, unless you are using something more advanced, there is also the pgrep command. "pgrep foo" will list all PIDs that have "foo" in the command.

The first line in your script could be more elegantly written as
```
LOAD=`pgrep internetcheck.jar | wc -l`
```

EDIT: An even more elegant solution:
```
if pgrep internetcheck.jar > /dev/null; then
	echo "Failed to launch: Internet Checker already running"
	exit 1
fi

echo "Running recheck..."
/home/windsor/workspaces/java/internetcheck.jar -rc
```

---

