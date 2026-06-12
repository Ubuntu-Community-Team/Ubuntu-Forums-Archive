---
title: "javac"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Souptik on 2011-01-17
Hello ! I am a beginner in java and have no idea how to use javac.....
Anyway i tried and got something like:
~$ javac /home/souptik/Desktop/ClockRotation
javac: invalid flag: /home/souptik/Desktop/ClockRotation
Usage: javac <options> <source files>
use -help for a list of possible options


Any way to get out of this fix....

---

### Post by Smart Viking on 2011-01-17
Hi quote from the javac man page:
```
Source code file names must have .java suffixes
```

So rename the java source files you want to compile with the correct suffix. You should read the manpage:
```
man javac
```

---

### Post by Souptik on 2011-01-17
Ok. working !!
but getting
Exception in thread "main" java.lang.NoClassDefFoundError: /home/souptik/Desktop/ClockRotation/java
Caused by: java.lang.ClassNotFoundException: .home.souptik.Desktop.ClockRotation.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: /home/souptik/Desktop/ClockRotation.java.  Program will exit.


Here's the source code:

import java.io.*;
public class ClockRotation
{
    public static void main(String[] args) throws IOException
    {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        System.out.print("Enter dimension of square array:");
        int n=Integer.parseInt(br.readLine());
        int a[][]=new int[n][n], temp=0, k=n-1, g=0, h=0, ctr=1;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
                a[i][j]=Integer.parseInt(br.readLine());
        }
        System.out.print("Enter the no.of times to rotate CW ::");
        int ro=Integer.parseInt(br.readLine());
        System.out.println("---------------------------------");
        System.out.println("Original matrix ::");
        System.out.println("---------------------------------");
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
              System.out.print(a[i][j]+" ");
            System.out.println();
        }
        System.out.println("---------------------------------");
        System.out.println("Rotated matrix ::");
        System.out.println("---------------------------------");
        while(ctr<=ro)
        {
            //transpose array
            for(int i=g;i<n;i++)
            {
                for(int j=h;j<n;j++)
                {
                    temp=a[i][j];
                    a[i][j]=a[j][i];
                    a[j][i]=temp;
                }
                g++;
                h++;
            }
            //rotating contents of each row
            for(int i=0; i<n ;i++)
            {
                for(int j=0; j<=n/2-1 ;j++)
                {
                    temp=a[i][j];
                    a[i][j]=a[i][k];
                    a[i][k]=temp;
                    k--;
                }
                k=n-1;
            }
            //reinitializing
            k=n-1;
            g=0;
            h=0;
            ctr++;
        }
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
                System.out.print(a[i][j]+" ");
            System.out.println();
        }
    }
}

---

