//Basic Web App for Codeship demo//
//published by Parrish Knowles//

package main

import (
				"fmt"
				"io/ioutil"
				"log"
				"net/http"
)
//Simple Go Web Server
func index_handler(w http.ResponseWriter, r *http.Request){
			fmt.Fprintf(w, "Hotdog is Not a Sandwich")
}

//This handles the http connection to the golang webserver localhost
func main() {
			http.HandleFunc("/", index_handler)
			log.Fatal(http.ListenAndServe(":9000", nil))
}


//Data Structure//
//Defining the page
type Page struct {
			Title string
			Body  []byte
}

//This will address persistant storage and does this method to save it on Page
func (p *Page) save() error {
			filename := p.Title + ".txt"
			return ioutil.WriteFile(filename, p.Body, 0600)
}

//This will laod the Page
func loadPage(title string) (*Page, error) {
			filename := title + ".txt"
			//The underscore is a "blank identifier" that is used to throw away  the return error
			body, err := ioutil.ReadFile(filename)
			if err != nil {
					return nil, err
			}
			return &Page{Title: title, Body: body}, nil
}

//Test func to test above code
func main() {
			p1 := &Page{Title: "Hotdog Page", Body: []byte("Hotdogs will NEVER BE A SANDWICH")}
			p1.save()
			p2, _ := loadPage("Hotdog Page")
			fmt.Println(string(p2.Body))
}
