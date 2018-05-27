# QUAD : [Q]uery [U]tility for [A]ccelerated [D]evelopment

## QUAD has four purposes:

- Inject knowledge into the Linux shell, available instantly [knowledge]
- Provide quick access to hundreds of oneliners you can expand on [access]
- Centralize commands to help anyone learn about them [centralization]
- Improve productivity using the Linux shell daily [productivity]

It is an effort to abstract and standardize usage of hundreds of commands
on the shell, but will ALSO allow *anyone* to actually learn what it can do.

If you've ever thought MS-DOS (or powershell) was nice,
wait until you see what the linux shell [and QUAD] has in store :)

Includes an Installer/Uninstaller, tested with bash shell on the following
platforms:

- Ubuntu based
- CentOS/RedHat based
- Arch Linux based

## REQUIREMENTS
- A Linux kernel and shell with autocomplete enabled
- Bash shell

NOTE: QUAD is extremely lightweight (<1mb) and does not use up any resources.

### Exclusions for now:
- Mac OS X - not tested yet
- Cygwin and Windows bash shell - not tested yet
- Raspberry Pi - not tested yet
- Docker containers - not tested yet
- Any other system not mentioned is untested for now

[Look at the contribute section below, if you would like to help test those]

## INSTALLATION

- Clone or download the repo above
- Open your Linux shell
- Go to the repo
- Run the installer as such:

./quad.sh install

When it runs the first time, QUAD detects the environment its running in and
injects tons of runnable commands (knowledge) into your shell.
It will provide accelerators so you don't have to type everything in long form.
As such, you should gain important productivity speed once you get
accustomed to it.

Everything is separated in different modules, such as:
- SYS (System commands)
- NET (Network commands)
- VIRT (Virtualization aware commands)
- etc.

The only hook it applies on your system is inside your ~/.bash_profile.
No need to have root/superuser (admin) status to install it.

## UNINSTALLING

./quad.sh uninstall
[Will leave QUAD in your system but will disable it on your next shell open]

## REMOVAL
Uninstall first [See above], then just remove the ~/quad and remove the link
~/.quad from your system; it's that easy. It does not leave files in the
operating system.

## UPGRADING
just update the repo using:
```
  $ cd ~/quad && git pull && q   <---> (or download the repo again on github)
```
NOTE: q command in the end will reload quad with new features.

## USAGE

[Remember: Do not type the dollar sign ($) below, it is there by default]

QUAD adds many new commands to your shell, available by typing queries
and then hitting [TAB] will autocomplete and show you the available commands.

After installing, type q. and the TAB key repeatedly until
you see the list of commands available to you.

FIRST TRY:

Type at your shell:
```
  $ q.status
```
      ... this shows you that QUAD is running, and its version.

Also, if you are unsure of a command or want to know if it even has the syntax you
want, or if you remember only partial information on what you're trying to do,
just use the "q.help" command to display what possibilities are offered,
such as:

```
$ q.help q.net.set

--------------------------------------------------------------------
[MODULE: NET]	q.net.ssh
		Opens ssh session [REQUIRES q.net.set.networkbits first!].

[MODULE: NET]	q.net.set.networkbits
		Sets the working network portion for easy ssh accesses.
--------------------------------------------------------------------
```

You can even go further by dumping the actual code
(for instance, before running), using q.dump

### EXAMPLE: Using q.dump to see underlying code
```
$ q.dump q.net.set.networkbits
```

```
q.net.set.networkbits is a function
q.net.set.networkbits ()
{
    q.co_green "EX: q.net.set.networkbits 192.168.1 [to focus on this network]";
    Q_NET_BITS=$1;
    export Q_NET_BITS
}
```

### EXAMPLE: Easily hash files in any directory for easy MD5 comparison

```
  $ q.app.md5sum-all-files
  ```


### EXAMPLE: Easily generating a password with 24 random characters
```
  $ q.app.password-generator 24
  ```
### TO DUMP THE ACTUAL CODE OF A QUAD FUNCTION:
    ```
    $ q.dump q.app.password-generator
    ...is a function
      dd if=/dev/urandom bs=1 count=$1 2> /dev/null | base64 -w 0 | rev | cut -b 2- | rev | sed 's/+/p/'
      ```
### TO ACCESS THE HELP MODULE ON THIS FUNCTION:
  ```
    $ q.help q.app.password-generator
      --------------------------------------------------------------------
      [MODULE:APP]	q.app.password-generator
		    Generates a good password. Expects a number of characters.

      --------------------------------------------------------------------
  ```

## WHY THIS PROJECT
It became evident to me over the years that people (especially those
new/interested to Linux) don't necessarily understand the power of the shell,
and/or are afraid to use it. Yes, the Linux shell represents some learning curve
but it should not deter people from using Linux. I firmly believe there are
missed opportunities because of that. I wish to give to the community a tool
to help anyone (not only IT professionals) trying to understand this amazing
piece of software that is the Linux shell, so Linux adoption can grow even
more over time. If you've never tried Linux, you should, it has an amazing
feature set (and GUI!) that surpasses (in my personal view) commercial paying
alternatives. If you don't know where to start and want something easy, that
ressembles MacOS/Windows, I humbly suggest starting with Ubuntu
at https://www.ubuntu.org


## HOW IT WORKS INTERNALLY
When loading your .bash_profile, QUAD will load hundreds of aliases and
functions that become available to you right away. It shouldn't take more than
1-2 seconds to load, even on poor performance hardware.

On github, the incubator branch is for development and PR, and the release
branch is for official releases.


## FUTURE EFFORTS
I wish to continue working on this project and add many more new features
into it. If you use it, find it useful and interesting, have an idea and want to
contribute, please drop me a line at quad at impossible3d dot com
with your feedback!

## CONTRIBUTE
You can contribute to QUAD by submitting your ideas/knowledge you would like it
to have. NOTE: New development from the community will happen in
the "incubator" directory in the incubator branch until it has been tested and
its added officially into the next QUAD release. Releases are in YEAR.MONTH
format so it's easy for QUAD to follow new software/technologies, and for you
to know you're using a current version. If your interest is such that you would
like to help QUAD project on github (not only technically), let me know at the
above address.

## LICENSE
PLEASE check the LICENSE file for details. But, in a nutshell:

### Permissions:
  - Private use
  - Commercial use
  - Distribution
  - Modification

### Conditions:
  - License must be included in subsequent work.

### Limitations:
  No Liability
  No Warranty

--------------------------------------------------------------------------------
### IMPORTANT: QUAD IS NOT RECOMMENDED FOR PRODUCTION WORK [YET]!
### BY CLONING/DOWNLOADING THIS REPO, YOU ACCEPT THAT YOU ARE USING QUAD AT
### YOUR OWN RISK.
--------------------------------------------------------------------------------
