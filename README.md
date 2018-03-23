###Usage
```sh
mussh [OPTIONS] <-h host.. | -H hostfile> [-c cmd] [-C scriptfile]
mussh --help        for full help text"

Send a command or list of commands to multiple hosts.
```

###OPTIONS

```sh
--help          This text.
-d [n]          Verbose debug.  Prints each action, all hosts
and commands to be executed to STDERR.  'n' can
be from 0 to 2.
-v [n]          Ssh debug levels.  Can be from 0 to 3.
-m [n]          Run concurrently on 'n' hosts at a time (asynchronous).
Use '0' (zero) for infinite. (default if -m)
-q              No output unless necessary.
-i <identity> [identity ..]
Load an identity file.  May be used
more than once.
-o <ssh-args>   Args to pass to ssh with -o option.
-a              Force loading ssh-agent.
-A              Do NOT load ssh-agent.
-b              Print each hosts' output in a block without mingling
with other hosts' output.
-B              Allow hosts' output to mingle. (default)
-u              Unique.  Eliminate duplicate hosts. (default)
-U              Do NOT make host list unique.
-P              Do NOT fall back to passwords on any host.  This will
skip hosts where keys fail.
-l <login>      Use 'login' when no other is specified with hostname.
-L <login>      Force use of 'login' name on all hosts.
-s <shell>      Path to shell on remote host. (Default: $REMOTE_SHELL)
-t <secs>       Timeout setting for each session.
(requires openssh 3.8 or newer)
-V              Print version info and exit.
```

###PROXY ARGS

```sh
        -p [user@]<host>
                        Host to use as proxy.  (Must have mussh installed)
        -po <ssh-args>        Args to pass to ssh on proxy with -o option.
```

###HOST ARGS

```sh
        -h [user@]<host> [[user@]<host> ..]
                        Add a host to list of hosts.  May be
                        used more than once.
        -H <file> [file ..]
                        Add contents of file(s) to list of hosts.
                        Files should have one host per line.  Use
                        \"#\" for comments.
```

###COMMAND ARGS

```sh
If neither is specified, commands will be read from standard input.
        -c <command>    Add a command or quoted list of commands and
                        args to list of commands to be executed on
                        each host.  May be used more than once.
        -C <file> [file ..]
                        Add file contents to list of commands to be
                        executed on each host.  May be used more
                        than once.
```
At least one host is required.  Arguments are in no particular order.

###EXAMPLES

```sh
mussh -H ./linuxhosts -C spfiles/testscript.sh
mussh -c \"cat /etc/hosts\" -h myhost.mydomain.com
```
