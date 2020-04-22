> I don't have time to get firmware engineers up to speed with websites. Here, use buffalo.

1. Install Golang
2. Install buffalo (gobuffalo.io)
3. Install Atom (atom.io) & https://github.com/bongnv/atom-ide-golang for code completion (follow instructions for adding the required packages)
	* go get -u golang.org/x/tools/cmd/goimports
	* go get -u github.com/nsf/gocode
	* go get -u github.com/zmb3/gogetdoc
	* go get -u golang.org/x/tools/cmd/guru
	* go get -u golang.org/x/lint/golint
	* go get -u github.com/ramya-rao-a/go-outline
4. you can also install a terminal (platformio-ide-terminal is nice)
3. Install docker and docker-compose
4. Install docker-machine & create a VM someplace (`docker-machine -d digitalocean --digitalocean-api-key $API_KEY create bob` or whatever then eval `docker-machine env bob`)
3. `buffalo new boiler --db-type=postgres` (that made this repo)
4. add a docker-compose with a preconfigured postgres database (see my example) (edit .env to add in the PG password and username and database and such...)
5. `go get -u -v github.com/gobuffalo/buffalo-plugins`, `buffalo plugins install`
6. `go get -u github.com/gobuffalo/buffalo-auth`, `buffalo plugins install github.com/gobuffalo/buffalo-auth`, `buffalo generate auth`
7. `buffalo g resource videocall`, `buffalo db migrate up`
8. `docker-compose up`
9. add SSL to your liking (cloudflare, traefik, nginx-letsencrypt, whatever you like)

something's broken? `buffalo fix` will kinda do a python2->3 migration of your code.

if you're curious about routes, in dev mode it'll print out what routes are defined and what variables are called. `buffalo routes`

why buffalo? it has an ORM with migration capability, it has CRUD resource generators
for boilerplate, it handles sessions, it can dump assets, it includes a UI,

**Heads Up** I'm still copying over my notes, so this code will be buggy.

# Welcome to Buffalo!

Thank you for choosing Buffalo for your web development needs.

## Database Setup

It looks like you chose to set up your application using a database! Fantastic!

The first thing you need to do is open up the "database.yml" file and edit it to use the correct usernames, passwords, hosts, etc... that are appropriate for your environment.

You will also need to make sure that **you** start/install the database of your choice. Buffalo **won't** install and start it for you.

### Create Your Databases

Ok, so you've edited the "database.yml" file and started your database, now Buffalo can create the databases in that file for you:

	$ buffalo pop create -a

## Starting the Application

Buffalo ships with a command that will watch your application and automatically rebuild the Go binary and any assets for you. To do that run the "buffalo dev" command:

	$ buffalo dev

If you point your browser to [http://127.0.0.1:3000](http://127.0.0.1:3000) you should see a "Welcome to Buffalo!" page.

**Congratulations!** You now have your Buffalo application up and running.

## What Next?

We recommend you heading over to [http://gobuffalo.io](http://gobuffalo.io) and reviewing all of the great documentation there.

Good luck!

[Powered by Buffalo](http://gobuffalo.io)
