# A24Studio Code Sniffer Coding Standards

Codesniffer is a tool used to detect coding standard violations in Php Projects. 

This project contains the coding standard rule to be used in PHP Code sniffer for any
project owned by A24Studio.

The standards are derived of PSR 0, 1 and 2 standards with additional checks on php docblock
comments.

# Dependencies

This coding standard is dependend on the PSR coding standards, the Generic standards, Zend coding standards
and PEAR coding standards. All these, except the PSR coding standards, are installed by default.

The PSR Coding standards can be found [here](git://github.com/klaussilveira/phpcs-psr.git). To install the PSR coding standards, I recommend following the commands below:
```bash
 cd /usr/share/php/PHP/CodeSniffer/Standards
 sudo git clone https://github.com/klaussilveira/phpcs-psr PSR
```
This will install the PSR coding standards on the system, but will not set them as the default.

# Installation
 * You will need to fork this repo
 * Clone your fork and add the required upstream
 * By Symlinking the project to the directory /usr/share/php/PHP/CodeSniffer/Standards
  * You can now modify the sniffs and create a PR (read copyright info) and changes are immediately available in your sniffs
  * Fetch the lastest changes from upstream and have them immediately available in your sniffs 

OR

To install the coding standards, do the following:
```bash
cd /usr/share/php/PHP/CodeSniffer/Standards
sudo git clone git@github.com:A24Group/A24StudioCS.git
```
## You must then
 * Set the A24Studio coding standards as the defaults, execute the following code:

```bash
sudo phpcs --config-set default_standard A24StudioCS
```
You will probably get an error of a file that does not exist.  Create the directory and file and try again.

 * You will also need to update your pre-commit hooks to use the new standards that have been created
edit the **config file** (not pre-commit file) in your git hooks, update the required line to:

```bash
PHPCS_CODING_STANDARD=A24StudioCS
```

# Code sniffer as a git pre-commit hook

## Installation

See instructions at https://github.com/s0enke/git-hooks/tree/master/phpcs-pre-commit. Please note that you will have to ensure that the pre-commit script is executable (`chmod +x` normally does the trick)

You will need to add this script to each project you wish to have tested against the standards.

You will also need to make the following change to the config file to tell the pre-commit hook to use the PSR standards installed on the pc.
```
PHPCS_CODING_STANDARD=A24StudioCS
```

## Usage

Now when ever you attempt to commit, the files you changed will be evaluated agains codesniffer. If any CS violations are found, the commit will terminate and these violations will be displayed to you. When using git-cola, these violations will display in the Command Output tab.
