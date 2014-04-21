
# CliTasks (clit)

clit is a Command-Line Interface Task/project manager

It is being developed with the following goals in mind:

* allow developers to view and manage tasks without breaking their workflow (leaving their terminal)
* decentralized - but can sync with a centralized master
    * similar to how local-copies of git repos float around
    * the list of "stories", who is working on what, and the status can follow the codebase or sync with a master repo
* clean document format - which is why I chose a custom Ruby DSL

# Show that it works

    ./bin/clit

# Example Story File:

    story 'Change the Homepage title to say "Foo"' do
      id 'ajsdfjsjs'
      status queued  # new is a reserved word
      created_by :unix_superhero
      assigned_to :unix_superhero, 'Foo Bar', :someone_else
      tags :test, 'tag_two', :three

      description <<-DESCRIPTION
        Lorem ipsum, and stuff...

        A long description can go here.
          
        To Do:
        * task one
        * task two
      DESCRIPTION

      comment 'Unix Superhero', <<-COMMENT
        Hai hai, sou desu ne?
      COMMENT

      comment 'Foo Bar', <<-COMMENT
        When will this be done?
      COMMENT
    end

# Future Plans

* REPL-style interactive console for viewing/updating stories
* Some intuitive story navigator, list by type, open in vim, etc.
* Web-interface/hosting for non-developers
* Shell integration
  * create new stories (clit create 'change the title on the homepage')
  * change their status (clit start a2c45a)
  * git/workflow integration (probably shouldn't be in the clit-core)
    * starting a story could create a feature branch
    * finishing it, merge into master? --don't like this
* Main stories/ directory with every story in it
  * rebuildable directory tree using symlinks
    * assigned/josh/\*
    * tag/homepage/\*
    * tag/other/\*
    * status/finished/\*
* Vim integration
  * commands/mappings to:
    * change a story's status, etc.
    * create a comment
  * netrw-style story navigation/organization
  * who knows?
