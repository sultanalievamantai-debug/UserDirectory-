let usersContainer = document.getElementById('users')
let searchInput = document.getElementById('search')
let countText = document.getElementById('count')

let allUsers = []

function renderUser(users) {
    usersContainer.innerHTML = ''
    countText.textContent = '   Найдено: ' + users.length
    users.forEach(function (one_user) {
        let card = document.createElement('div')
        card.classList.add('card')
        let status = one_user.isOnline ? '🟢 Онлайн' : '⚪ Офлайн'
        let skillsHtml = one_user.skills.map(function (skill) {
            return '<span class="skill">' + skill + '</span'
        }).join('')
        card.innerHTML = `
            <div class="avatar">${one_user.avatar}</div>
            <h3>${one_user.name}</h3>
            <p>Возраст: ${one_user.age}</p>
            <p>Город: ${one_user.city}</p>
            <p>Email: ${one_user.email}</p>
            <p>${status}</p>
            <div>${skillsHtml}</div>
        `
        usersContainer.appendChild(card)
    });
}

fetch('users.json')
    .then(function (response) {
        return response.json()
    })
    .then(function (data){
        allUsers = data
        renderUser(allUsers)
    })
    .catch(function(){
        usersContainer.textContent = 'Ошибка загрузки: ' + error.message
    })

searchInput.addEventListener('input', function() {
    let query = searchInput.value.toLowerCase()
    let filtered = allUsers.filter(function (user) {
        return user.name.toLowerCase().includes(query)
    })
    renderUser(filtered)
})
