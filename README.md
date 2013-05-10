#Useful Git Hooks#
A collection of git hook scripts and related utility scripts used by myself in
my own repositories.  Many of them are hand-configured for specific
repositories, and so should be modified before use.

## Adding it to your repository ##
Feel free to re-use this set of hooks to build latex documents in your own git
repository.

### Prerequisites ###
The following are required for repository host and repository:
* The repository host must be able to send emails.
* The following software packages: sendmail, Make, LaTeX.
* The LaTeX document should have a makefile with a target called "pdf". No
	other PDF documents should be in the output directory of the project.
* The repository host hould have a webserver and the repository account should
	have a directory where it can place files for the web server. This is
	typically in a "public_html" subdirectory.

### Installation ###
1. Copy hooks/post-receive to your hooks/ subdirectory of the bare repository.
	 Make it executable.
1. Copy the post-receive-email and post-receive-pdflatex somewhere that the
	 Git user can access them.  I use $HOME/githooks.
1. Add a file named 'description' in your bare repository.  It should have a
	 single line of text containing the repository name.
1. Update the file 'config' in your bare repository with the following:
      [hooks]
			  mailinglist = user@host.com,user@host2.com
				emailprefix = "Quotes Preserve Spaces "
		Note that the quotes aren't necessary, but will preserve the trailing
		space.
1. Update the various scripts as appropriate for your host/repository.  I may
	 add placeholders/tips to this README at a later date.

## Usage ##
Every time you push one or more commits (in any branch) into your repository,
it will build the PDF, copy it to the web server directory, and then send the
email.  You should also get the URL on your console when you push.

## Support ##
Contact me on github and I will see what I can do. 
